---
title: "Intro to Linux — Workshop for CS Students"
theme: "serif"
highlightTheme: "monokai"
transition: "fade"
marp: true
---

# Intro to Linux


---

##  What *is* Linux?

- **Linux** = the *kernel* (manages hardware & processes)
- **Distribution (Distro)** = kernel + userland + package manager  
  → Examples: Ubuntu, Fedora, Arch, Debian  
- **GNU/Linux** = Linux kernel + GNU userland  
- Command line is a *first-class interface*
> What your username and distro are:
```bash
uname -a
cat /etc/os-release
```
>There are more ~~sweaty~~ _fancy_ ways to show system information, like `neofetch` and `fastfetch`, but these are kind of performative...

---

##  Shells, Terminals, and TTYs

- **TTY** → “Teletypewriter” (historical terminal interface)
- Modern systems use **virtual TTYs** (`/dev/tty1`, `/dev/pts/0`, etc.)
- **Shell** = command interpreter (bash, zsh, fish)
- **Terminal emulator** = GUI window that runs a shell
- You type → shell interprets → kernel executes

```bash
tty
ps -p $$
echo $SHELL
```

>  Concept map: **Terminal → Shell → Kernel**

---

##  Filesystem & Navigation

**Everything is a file**

- Hierarchical structure rooted at `/`
- Key directories:
  - `/home` – user data  
  - `/etc` – configuration  
  - `/usr` – shared programs  
  - `/dev` – devices  
  - `/var` – variable data

```bash
pwd
ls -la
cd /usr
tree
find . -name "*.txt"
```

> `/dev/null` is a file — but acts like a black hole!

---

## Working with Files

**Creating, Viewing, and Editing**

```bash
touch notes.txt
echo "Hello Linux" > notes.txt
cat notes.txt
head -n 3 file.txt
tail -n 2 file.txt
less longfile.txt
```

**Moving and Deleting**

```bash
cp file1 file2
mv file1 folder/
rm file1
```

 *Challenge:* Create a file, add 5 lines, and show only the first 3.

---

##  Disk & Storage Utilities

**How Much Space Am I Using?**

`du` → Disk Usage  
```bash
du -sh ~/*
```

`df` → Disk Free  
```bash
df -h
```

| Tool | Purpose |
|------|----------|
| `du` | Space used by files/directories |
| `df` | Space available on filesystems |

>  Compare results — they measure different things!

---

##  Users & Permissions

- Every file has:
  - **Owner**
  - **Group**
  - **Permissions** (`rwxr-xr--`)
- `sudo` lets you run commands as root

```bash
whoami
ls -l
chmod +x script.sh
sudo command
```

> Execute permission (`x`) means a script can be run.
> Write permission (`w`) means a script can be written/edited

---

##  Desktop Environments vs Window Managers

| Layer | Function | Examples |
|-------|-----------|-----------|
| **Kernel** | Core OS | Linux |
| **Init/System Manager** | Starts & monitors services | systemd |
| **Display Server** | Draws to screen | Xorg, Wayland |
| **Window Manager (WM)** | Handles window placement | i3, Mutter, hyprland, COSMIC |
| **Desktop Environment (DE)** | Full UX + WM + apps | GNOME, KDE, XFCE |

>  DE = “entire room” (furniture, lighting, walls)  
> WM = “just the windows”

---

##  Processes & System Info

- Each process has a PID (Process ID)
- `PID 1` = first process (usually `systemd`)

```bash
ps aux | head
top
pstree -p
uptime
free -h
```

>  Use `kill` to send signals to processes.

---



### Pipelines & Redirection

```bash
cat file | grep "error" > results.txt
```

### Text Processing
```bash
grep keyword file.txt
awk '{print $1}'
sed 's/foo/bar/g'
```

### Networking
```bash
ping example.com
curl https://example.com
wget https://example.com/file.txt
```

#####  Fun Nonsense
```bash
neofetch
cowsay "Hello Linux!"
fortune | cowsay
```

---

##  Wrap-Up & Mini Challenges

- Linux is modular — everything is transparent & scriptable
- Use the terminal to:
  - Explore your system
  - Automate tasks
  - Understand OS design

###  Mini Challenges
1. Find the 3 largest files in your `home` directory  
2. Display the 5 most memory-hungry processes  
3. Count all `.txt` files recursively



### Cool Packages

- `tldr` de-yaps manpages, which is always appreciated
- `tree` gives you a tree-based output of your `pwd`



---
