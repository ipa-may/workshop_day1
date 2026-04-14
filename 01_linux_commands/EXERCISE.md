# Linux Commands Exercise

Goal:

1. Create a folder called `ws_linux_command`
2. Inside it, create a folder called `src`
3. Go to the folder `my_bash_to_copy`
4. Copy the bash script into `ws_linux_command/src`
5. Run the script so that it prints `Hello world`

## Instructions

Start in the `01_linux_commands` folder.

1. Create the workspace folder:

```bash
mkdir -p ws_linux_command/src
```

2. Check where you are:

```bash
pwd
```

3. Go to the folder containing the script:

```bash
cd my_bash_to_copy
```

4. Check your location again:

```bash
pwd
```

5. Copy the script into `src`:

```bash
cp hello_world.sh ../ws_linux_command/src/
```

6. Go to the destination folder:

```bash
cd ../ws_linux_command/src
```

7. Check the file permissions:

```bash
ls -l
```

8. Make the script executable and run it:

```bash
chmod +x hello_world.sh
ls -l
./hello_world.sh
```

Expected output:

```text
Hello world
```

## Hint

Use `pwd` often. It helps you understand where you are.

If you use Terminator, keep one terminal in `my_bash_to_copy` and one terminal in `ws_linux_command/src`. See [TERMINATOR.md](./TERMINATOR.md).
