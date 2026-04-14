# Network basics on Ubuntu

This page introduces a few basic network commands that are useful on Linux.


## What is a network?

A network is a connection between computers so they can exchange data.

Examples:

- your laptop connected to the workshop Wi-Fi
- your PC connected to a robot over Ethernet
- one computer connecting to another with `ssh`

Each device on a network usually has an IP address such as `192.168.1.10`. You can think of the IP address as the network address of that machine.

## `ping`

`ping` checks whether another machine can be reached over the network.

Example:

```bash
ping 8.8.8.8
```

You can also ping a hostname:

```bash
ping google.com
```

Example pinging anothere pc:
```bash
ping 192.168.1.42
```

If the machine is reachable, you will see replies and timing information.

Example output:

```text
64 bytes from 192.168.1.42: icmp_seq=1 ttl=64 time=1.23 ms
```

Useful points:

- if `ping` works, the target machine is reachable at the network level
- if it does not work, the machine may be offline, on a different network, or blocked by a firewall
- stop `ping` with `Ctrl + C`

## `ifconfig`

`ifconfig` shows network interface information such as IP addresses.

Example:

```bash
ifconfig
```

This command may show interfaces such as:

- `lo` for the local loopback interface
- `wlan0` or similar for Wi-Fi
- `eth0` or similar for Ethernet

You may see an address like:

```text
inet 192.168.1.23
```

That is the IP address of your machine on that network.

Important note:

- on modern Ubuntu, `ifconfig` is considered older and may not be installed by default
- the newer command is usually `ip addr`

Equivalent modern command:

```bash
ip addr
```

## `ssh`

`ssh` means Secure Shell. It lets you open a terminal on another computer over the network.

Example:

```bash
ssh user@192.168.1.42
```

This means:

- connect to the machine at `192.168.1.42`
- log in as user `user`

The first time you connect, Linux may ask whether you trust the remote host. After that, it will usually ask for the password unless SSH keys are configured.

Typical uses:

- log in to a robot PC
- log in to another Ubuntu machine
- run commands remotely without sitting in front of that computer

To leave the remote session:

```bash
exit
```

## `scp`

`scp` means Secure Copy. It copies files over SSH.

Copy a file from your machine to another machine:

```bash
scp my_file.txt user@192.168.1.42:/home/user/
```

Copy a file from another machine to your machine:

```bash
scp user@192.168.1.42:/home/user/my_file.txt .
```

The final `.` means "copy into the current directory".

You can also copy folders with `-r`:

```bash
scp -r my_folder user@192.168.1.42:/home/user/
```

## Questions

Connect to the ros-industrial network.

Your IP address should be `192.168.3.X`.

What is your IP?
Can you ping your neighbors?
