# Start here: Git & GitHub from zero

Hi Daniel 👋 This guide takes you from "never used Git" to "I can share my changes with Guillaume".
It takes about 30 minutes the first time. You only do Parts 1–3 once.

---

## Part 0: What is this stuff?

- **Git** is a program on your computer that remembers every version of the files in a folder.
  Each saved version is called a **commit**: a snapshot plus a short note about what changed.
- **GitHub** is a website that keeps a copy of that folder online, so several people can share it.
- A folder tracked by Git is called a **repository** (or **repo**).

The whole workflow is three moves:

| Move | What it means |
|------|---------------|
| **pull** | Download the latest changes from GitHub to your computer |
| **commit** | Save a snapshot of your own changes on your computer |
| **push** | Upload your commits to GitHub so Guillaume gets them |

---

## Part 1: Create a GitHub account

1. Go to <https://github.com/signup> and create a free account.
2. Pick a username you're happy with, because people will see it.
3. **Send your username to Guillaume.** He'll invite you to the project.
4. You'll get an email invitation (or see it at <https://github.com/notifications>). **Accept it.**
   Until you accept, you can look at the project but not push to it.

---

## Part 2: Install the tools

You need two programs: **Git** and the **GitHub CLI** (`gh`), which handles logging in for you.

### On Windows

1. Install Git: <https://git-scm.com/download/win>. Download it, run it, and click *Next* on every screen (the defaults are fine).
2. Install GitHub CLI: <https://cli.github.com>. Download the Windows installer and run it.
3. Open the program called **Git Bash** (search for it in the Start menu). That's your terminal from now on.

### On Mac

1. Open the **Terminal** app (press Cmd+Space and type "Terminal").
2. Type `git --version` and press Enter. If macOS offers to install "command line developer tools", click **Install**.
3. Install GitHub CLI: download the macOS installer from <https://cli.github.com> and run it.

### Check that it worked

Close and reopen your terminal, then type these one at a time (press Enter after each):

```bash
git --version
gh --version
```

Each should print a version number. If you see "command not found", restart the computer and try again.

> 💡 **Terminal tips:** You type a command and press Enter. Commands are case-sensitive.
> To paste in Git Bash, use **Shift+Insert** or right-click → Paste.

---

## Part 3: One-time setup

### Tell Git who you are

This name and email get attached to your commits. Use the same email as your GitHub account:

```bash
git config --global user.name "Daniel Yourlastname"
git config --global user.email "you@example.com"
```

### Log in to GitHub

```bash
gh auth login
```

It asks a few questions. Use the arrow keys and Enter to answer:

- *Where do you use GitHub?* → **GitHub.com**
- *Preferred protocol?* → **HTTPS**
- *Authenticate Git with your GitHub credentials?* → **Yes**
- *How would you like to authenticate?* → **Login with a web browser**

It shows a code. Press Enter, your browser opens, you paste the code and approve. Done.

### Download the project

Pick where you want the folder to go. For example, this puts it in your home folder:

```bash
cd ~
git clone https://github.com/guillaumekuc/shared-with-daniel.git
cd shared-with-daniel
```

You now have a folder called `shared-with-daniel` with all the files in it.
You can open it in your normal file explorer and edit files with any text editor.

> 💡 `cd` means "change directory" (go into a folder). `cd ~` goes to your home folder.
> Every time you open a new terminal, run `cd ~/shared-with-daniel` to get back into the project.

---

## Part 4: Your first change 🎉

1. **Get the latest version** (always do this first):
   ```bash
   git pull
   ```
2. **Make a change.** Open `guestbook.md` in a text editor, add a line at the bottom like
   `- Daniel: I did it!`, and save the file.
3. **See what changed:**
   ```bash
   git status
   ```
   It lists `guestbook.md` in red as "modified".
4. **Stage the change** (mark it to go into the next snapshot):
   ```bash
   git add .
   ```
   The `.` means "everything I changed in this folder". Run `git status` again and it's green now.
5. **Commit** (take the snapshot, with a short note):
   ```bash
   git commit -m "Sign the guestbook"
   ```
6. **Push** (send it to GitHub):
   ```bash
   git push
   ```

Now open <https://github.com/guillaumekuc/shared-with-daniel> in your browser. Your change is there. Guillaume gets it the next time he runs `git pull`.

---

## The everyday routine (cheat sheet)

```bash
cd ~/shared-with-daniel     # go to the project
git pull                    # 1. get Guillaume's latest changes
# ... edit files ...
git add .                   # 2. stage your changes
git commit -m "what I did"  # 3. snapshot with a note
git push                    # 4. share it
```

Handy extras:

```bash
git status      # what's changed? (use it all the time, it's harmless)
git log --oneline   # list of past commits (press q to quit)
```

---

## When something goes wrong

**`git push` says "rejected" / "fetch first" / "non-fast-forward".**
Guillaume pushed something since your last pull. Run `git pull`, then `git push` again.

**A weird text editor opened after `git pull`** (a screen full of `~` characters, or a message about "merge").
Git wants a note for combining your work with Guillaume's. The default note is fine.
- If you see `~` characters on the left (this is vim): type `:wq` and press Enter.
- If the bottom says `^X Exit` (this is nano): press Ctrl+X.

**"CONFLICT" after `git pull`.**
You and Guillaume edited the same lines. Open the file and you'll see something like:

```
<<<<<<< HEAD
your version
=======
Guillaume's version
>>>>>>> ...
```

Edit it to what it should be, delete the `<<<<<<<`, `=======` and `>>>>>>>` lines, save, then:

```bash
git add .
git commit -m "Fix conflict"
git push
```

**"Permission denied" or 403 on push.**
You haven't accepted Guillaume's invitation yet (see Part 1), or you need to run `gh auth login` again.

**"not a git repository".**
You're in the wrong folder. Run `cd ~/shared-with-daniel`.

**Totally stuck?**
Don't panic, because nothing here can be permanently broken. Copy what the terminal says and send it to Guillaume.
