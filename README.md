# bashtoys
A collection of highly useful bash scripts

These scripts are designed for systems using the GNU Bash shell (e.g., Ubuntu, Debian, Fedora, Arch, macOS, WSL), and will run in any terminal emulator that launches Bash.

DISCLAIMER: These scripts are provided "AS IS" without warranty of any kind. The author assumes no responsibility for any consequences of their use.

How do I add these scripts to my bashrc file? [Go to Nano Instructions](#add-code-with-nano)

# The list

[Lastpath](#lastpath)
Gets the last absolute path used in the terminal and opens it in the default file manager.

# Lastpath

Gets the last absolute path used in the terminal and opens it in the default file manager. If no path is found, the script opens the current directory.

Works on most Linux distributions that support the XDG desktop standards and include xdg-open (e.g., Ubuntu, Debian, Fedora, Arch, etc.).

```bash
lastpath() {
    # Get the last command
    last_cmd=$(history | tail -n2 | head -n1 | sed 's/^[ ]*[0-9]\+[ ]*//')

    # Extract first absolute path
    path=$(echo "$last_cmd" | grep -o '/[^ ]*' | head -n1)

    # If no path found, use current directory
    if [ -z "$path" ]; then
        path=$(pwd)
    fi

    xdg-open "$path"
}
```

Usage example.
```bash
$ cd /usr/share/doc
$ ls
$ lastpath
```




# Add code with nano

Here's a brief walkthrough of adding code to `.bashrc` via nano:

1. Open nano editor by running:

```bash
nano ~/.bashrc
````

2. Scroll to the bottom of the file.

3. Add your new code on a new line, for example:

```bash
# New addition
echo "Hello World"
```

4. Save and exit nano by pressing **Ctrl+X**, then **Y**, then **Enter**.

5. Reload `.bashrc` to apply changes:

```bash
source ~/.bashrc
```

**Key points:**

* `.bashrc` is a hidden file in your home directory (`~/.bashrc`)
* Use `nano ~/.bashrc` to open/edit it
* Add your new code at the end of the file
* Save with **Ctrl+X**, then **Y**, then **Enter**
* Reload with `source ~/.bashrc`

It's recommended to backup `.bashrc` before making major changes:

```bash
cp ~/.bashrc ~/.bashrc.bak
```

This creates a copy named `.bashrc.bak` in the same directory.

