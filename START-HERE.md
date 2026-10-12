# Start here: Git & GitHub from zero

🇫🇷 *Version française : [COMMENCER-ICI.md](COMMENCER-ICI.md)*

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

1. **Install Git:** <https://git-scm.com/download/win>
   Download it and run the installer. Click *Next* on every screen, **except one**:
   on the *"Choosing the default editor used by Git"* screen, pick **"Use Notepad as Git's default editor"**.
   (The default is an editor called Vim that is confusing for beginners.)
2. **Install GitHub CLI:** <https://cli.github.com>
   Download the Windows installer and run it.
3. **Open Git Bash.** Search for "Git Bash" in the Start menu. That's your terminal from now on.

### Check that it worked

Type these one at a time (press Enter after each):

```bash
git --version
gh --version
```

Each should print a version number. If you see "command not found", close Git Bash and open it again.
If that doesn't help, restart the computer.

> 💡 **Terminal tips:** You type a command and press Enter. Commands are case-sensitive.
> To paste in Git Bash, use **Shift+Insert** or right-click → Paste. (Ctrl+V doesn't work there.)

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

```bash
cd ~
git clone https://github.com/guillaumekuc/shared-with-daniel.git
cd shared-with-daniel
```

This creates a `shared-with-daniel` folder in your user folder (`C:\Users\YourName\shared-with-daniel`).
You can open it in File Explorer and edit the files with any text editor (Notepad works fine).

> 💡 `cd` means "change directory" (go into a folder). `cd ~` goes to your user folder.
> Every time you open Git Bash, run `cd ~/shared-with-daniel` to get back into the project.

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
git status          # what's changed? (use it all the time, it's harmless)
git log --oneline   # list of past commits (press q to quit)
```

---

## Bonus: Git with buttons instead of commands (GUIs)

Once the terminal routine makes sense, you can use a **Git GUI**: an app that does the same
pull / commit / push with buttons and shows your changes visually. It's the same Git underneath,
so you can switch between the terminal and a GUI whenever you like.

- **[Sublime Merge](https://www.sublimemerge.com)** is what Guillaume uses, so he can help you with it. It's fast and clean.
  It's free to try with no time limit, and only shows an occasional reminder to buy a licence.
- **[GitHub Desktop](https://desktop.github.com)** is free, made by GitHub, and very beginner-friendly.

To use either one, open the `shared-with-daniel` folder you already cloned
(*File → Open Repository* in Sublime Merge, *File → Add local repository* in GitHub Desktop).

> 💡 Learn the commands first anyway. They help you understand what the buttons do,
> and when something goes wrong, error messages and help online are written in terms of commands.

---

## When something goes wrong

**`git push` says "rejected" / "fetch first" / "non-fast-forward".**
Guillaume pushed something since your last pull. Run `git pull`, then `git push` again.

**Notepad opened by itself after `git pull`.**
Git wants a note for combining your work with Guillaume's. The default text is fine:
just close Notepad (save if it asks), and Git continues.

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

(GUIs like Sublime Merge make conflicts easier to see and fix.)

**"Permission denied" or 403 on push.**
You haven't accepted Guillaume's invitation yet (see Part 1), or you need to run `gh auth login` again.

**"not a git repository".**
You're in the wrong folder. Run `cd ~/shared-with-daniel`.

**Totally stuck?**
Don't panic, because nothing here can be permanently broken. Copy what the terminal says and send it to Guillaume.
