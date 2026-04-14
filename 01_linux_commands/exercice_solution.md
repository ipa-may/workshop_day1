# Exercice solution

Start in the `01_linux_commands` folder.

In the first terminal:

```bash
mkdir -p ws_linux_command/src
cd ws_linux_command/src
pwd
```

In the second terminal:

```bash
cd my_bash_to_copy
pwd
ls
```

From the second terminal, copy the script:

```bash
cp hello_world.sh ../ws_linux_command/src/
```

Then in the first terminal, run:

```bash
ls
chmod +x hello_world.sh
./hello_world.sh
```

Expected output:

```text
Hello world
```

## Tip

If you are unsure where a folder is, run:

```bash
pwd
```

This prints the full path of your current directory.
