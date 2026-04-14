# Basic Linux Commands

This folder contains a short introduction to the Linux terminal for the ROS workshop.

## What is a terminal?

The terminal is a text-based way to interact with your computer. In ROS, you will use it a lot to navigate folders, create files, run scripts and start nodes.

## Commands to know

`pwd`

Prints the current working directory.

Example:

```bash
pwd
```

`ls`

Lists the files and folders in the current directory.

Example:

```bash
ls
```

`cd`

Changes directory.

Examples:

```bash
cd 01_linux_commands
cd ..
```

`mkdir`

Creates a new directory.

Example:

```bash
mkdir ws_linux_command
```

`mkdir -p`

Creates nested directories in one command.

Example:

```bash
mkdir -p ws_linux_command/src
```

`cp`

Copies a file.

Example:

```bash
cp hello_world.sh ../ws_linux_command/src/
```

`mv`

Moves or renames a file or folder.

Examples:

```bash
mv hello_world.sh hello.sh
mv hello.sh ../ws_linux_command/src/
```

`sudo`

Runs a command with administrator privileges.

Example:

```bash
sudo apt update
```

Use `sudo` only when it is really needed, for example when installing software or changing system-wide settings.

Be careful:

- `sudo` gives very strong permissions
- a wrong command with `sudo` can change or damage the system
- for normal work in your home folder, you usually do not need it

`chmod +x`

Makes a script executable.

Example:

```bash
chmod +x hello_world.sh
```

`ls -l`

Lists files in long format. This shows extra information such as permissions, owner, size, and modification date.

Example:

```bash
ls -l
```

Example output:

```text
-rw-rw-r-- 1 user user 29 Apr 13 10:00 hello_world.sh
```

How to read `-rw-rw-r--`:

- the first character tells the type: `-` means regular file, `d` means directory
- the next three characters are the permissions for the owner: `rw-`
- the next three characters are the permissions for the group: `rw-`
- the last three characters are the permissions for others: `r--`

Meaning of each letter:

- `r` means read
- `w` means write
- `x` means execute
- `-` means that permission is not given

So `-rw-rw-r--` means:

- owner can read and write
- group can read and write
- others can only read

For a script to run directly with `./hello_world.sh`, it usually needs execute permission. You can add that with:

```bash
chmod +x hello_world.sh
ls -l
```

`./file_name`

Runs an executable file in the current directory.

Example:

```bash
./hello_world.sh
```

You can also run a script with:

```bash
bash hello_world.sh
```

## Tip

Use `pwd` often. It helps you understand where you are before using `cd` or `cp`.

For the hands-on task, see [EXERCISE.md](./EXERCISE.md).

For working with multiple terminals at the same time, see [TERMINATOR.md](./TERMINATOR.md).
