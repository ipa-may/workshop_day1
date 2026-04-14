# Git Exercise

## Goal

In this exercise you will:

1. Clone the workshop repository
2. Navigate into the repository
3. Create a new branch called `workshop_<number>`
4. Create a file called `hello.txt`
5. Add the file to Git
6. Create a commit

## Repository

Clone this repository:

```bash
https://github.com/ipa-may/workshop_day1.git
```

## Instructions

1. Go into the `02_git` folder:

```bash
cd /home/ros2-04/WS_WORKSHOP/day_1/02_git
```

2. Clone the repository:

```bash
git clone https://github.com/ipa-may/workshop_day1.git
```

3. Navigate into the cloned repository:

```bash
cd workshop_day1
```

4. Create your own branch:

Replace `<number>` with your participant number.

```bash
git checkout -b workshop_<number>
```

5. Create a file called `hello.txt`:

```bash
touch hello.txt
```

6. Check the repository status:

```bash
git status
```

7. Add the file to Git:

```bash
git add hello.txt
```

8. Create a commit:

```bash
git commit -m "Add hello.txt"
```

9. Check the history:

```bash
git log --oneline
```

## Optional

If your repository is connected to a remote and you have access, you can push your branch:

```bash
git push -u origin workshop_<number>
```

## Tip

Run `git status` often. It is the easiest way to understand what Git sees in your repository.
