# bashtoys
A collection of highly useful bash scripts

These scripts are designed for systems using the GNU Bash shell (e.g., Ubuntu, Debian, Fedora, Arch, macOS, WSL), and will run in any terminal emulator that launches Bash.

## DISCLAIMER: These scripts are provided "AS IS" without warranty of any kind. The author assumes no responsibility for any consequences of their use.

# Lastpath

Gets the last absolute path used in the terminal and opens it in the default file manager.

Works on most Linux distributions that support the XDG desktop standards and include xdg-open (e.g., Ubuntu, Debian, Fedora, Arch, etc.).

''' lastpath() {
    # Get the last command
    last_cmd=$(history | tail -n2 | head -n1 | sed 's/^[ ]*[0-9]\+[ ]*//')

    # Extract first absolute path
    path=$(echo "$last_cmd" | grep -o '/[^ ]*' | head -n1)

    # If no path found, use current directory
    if [ -z "$path" ]; then
        path=$(pwd)
    fi

    xdg-open "$path"
} '''

