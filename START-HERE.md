# Start here: Git & GitHub from zero

🇫🇷 *Version française : [COMMENCER-ICI.md](COMMENCER-ICI.md)*

Hi Daniel 👋 This guide takes you from "never used Git" to "I can share my changes with Guillaume".

We start **with an app that has buttons** (Sublime Merge, the one Guillaume uses).
Once you're comfortable, we'll do **the same moves on the command line** (level 2, at the end).

It takes about 30 minutes the first time. You only do Parts 1–3 once.

---

## Part 0: What is this stuff?

- **Git** is a program that remembers every version of the files in a folder.
  Each saved version is called a **commit**: a snapshot plus a short note about what changed.
- **GitHub** is a website that keeps a copy of that folder online, so several people can share it.
- A folder tracked by Git is called a **repository** (or **repo**).
- **Sublime Merge** is an app that lets you use Git with buttons instead of typing commands.

The whole workflow is three moves:

| Move | What it means |
|------|---------------|
| **Pull** | Download the latest changes from GitHub to your computer |
| **Commit** | Save a snapshot of your own changes on your computer |
| **Push** | Upload your commits to GitHub so Guillaume gets them |

---

## Part 1: Create a GitHub account

1. Go to <https://github.com/signup> and create a free account.
2. Pick a username you're happy with, because people will see it.
3. **Send your username to Guillaume.** He'll invite you to the project.
4. You'll get an email invitation (or see it at <https://github.com/notifications>). **Accept it.**
   Until you accept, you can look at the project but not push to it.

---

## Part 2: Install the tools

1. **Install Git:** <https://git-scm.com/download/win>
   Download it and run the installer. Click *Next* on every screen, **except one**:
   on the *"Choosing the default editor used by Git"* screen, pick **"Use Notepad as Git's default editor"**.
   (The default is an editor called Vim that is confusing for beginners.)
   Git also includes the small tool that handles signing in to your GitHub account.
2. **Install Sublime Merge:** <https://www.sublimemerge.com/download>
   Get the Windows version and run the installer.
   It's free to try with no time limit. It only shows an occasional reminder to buy a licence, which you can close.

---

## Part 3: One-time setup

### Tell Git who you are

Your name and email get attached to each of your commits. These are the only two commands
in the guide before level 2, and you can just copy and paste them.

1. In the Start menu, search for and open **Git Bash** (a black window opens).
2. Copy the first line below, paste it with **Shift+Insert** (or right-click → Paste), put in your name, and press Enter.
3. Do the same with the second line, using **the same email as your GitHub account**.

```bash
git config --global user.name "Daniel Yourlastname"
git config --global user.email "you@example.com"
```

You can close Git Bash.

### Download the project ("clone" it)

1. Open **Sublime Merge**. You land on the welcome page:

   ![Sublime Merge welcome page](https://www.sublimemerge.com/images/clone_page.png)

2. Click **Clone Repository** (or use the menu *File → Clone Repository…*).
3. Fill in the fields:
   - **Source URL:** `https://github.com/guillaumekuc/shared-with-daniel.git`
   - **Destination Path:** where the folder should go, e.g. `C:\Users\YourName\shared-with-daniel`
4. Click **Clone**. The project opens in Sublime Merge.

The `shared-with-daniel` folder now exists on your computer. You can open it in File Explorer
and edit the files with any text editor (Notepad works fine).

### A quick tour

![Sublime Merge overview](https://www.sublimemerge.com/images/overview.png)

- **In the middle:** the history, which is the list of commits, newest first.
  The **Working Directory** line at the very top stands for your changes that aren't committed yet.
- **Top right:** the **Pull** and **Push** buttons.

![Pull and Push buttons](https://www.sublimemerge.com/images/push_and_pull.png)

---

## Part 4: Your first change 🎉

1. **Get the latest version:** click **Pull** (top right). *Always* do this first.
2. **Make a change.** In File Explorer, open `guestbook.md` with Notepad.
   Add a line at the bottom like `- Daniel: I did it!` and save.
3. **Go back to Sublime Merge.** Click the **Working Directory** line at the top of the history.
   `guestbook.md` shows up under **Unstaged Files** (changed but not prepared yet).
   Added lines are green and removed lines are red.
4. **Prepare the change ("Stage"):** click the **Stage** button next to the file
   (or **Stage All** to prepare everything at once). The file moves to **Staged Files**.

   ![Files to stage](https://www.sublimemerge.com/images/file_tabs.png)

5. **Commit:** at the very top, type a short note in the message box,
   e.g. `Sign the guestbook`, then click **Commit**.

   ![Commit message box](https://www.sublimemerge.com/images/commit_message.png)

   Your commit now appears at the top of the history. It's still **only on your computer**.

6. **Send it ("Push"):** click **Push**.
   **The very first time**, a GitHub window opens so you can sign in: choose
   **Sign in with your browser**, log in in the browser and approve. You won't be asked again after that.

Now open <https://github.com/guillaumekuc/shared-with-daniel> in your browser. Your change is there.
Guillaume gets it the next time he clicks Pull.

---

## The everyday routine

1. **Pull** to get Guillaume's latest changes
2. Edit files (in your usual editor)
3. In Sublime Merge: **Stage** the files
4. Type a message, then **Commit**
5. **Push**

That's it. These 5 steps cover 95% of what you'll need.

---

## When something goes wrong

**Push is rejected ("rejected", "fetch first", "non-fast-forward").**
Guillaume pushed something since your last Pull. Click **Pull**, then **Push** again.

**"Conflict" after a Pull.**
You and Guillaume edited the same lines, and Git doesn't know which version to keep.
In Sublime Merge the file shows up in a **Merge Conflicts** section. Open it in the merge tool:

![Merge conflict tool](https://www.sublimemerge.com/images/merge_tool.png)

Your version and Guillaume's are side by side, with the result in the middle.
Choose which version to keep for each part, save, then **Stage**, **Commit** and **Push** as usual.
If you're unsure, ask Guillaume. It's easier with two people the first time.

**Push asks for a password, or says "Permission denied" / 403.**
- Check that you accepted Guillaume's invitation (see Part 1).
- Check that Git is installed (Part 2), because it's what shows the GitHub sign-in window.
- If it still fails: in Sublime Merge, open *Preferences → Advanced* (or *Tools → Preferences*),
  find the **Git Binary** setting, set it to **System**, and try again.

**Totally stuck?**
Don't panic, because nothing here can be permanently broken. Take a screenshot and send it to Guillaume.

---

## Level 2: the same thing on the command line

Once the button routine feels natural, learn the commands.
It's worth it: error messages and online help are almost always written in terms of commands,
and you'll understand what the buttons actually do. It's the same Git underneath,
so you can switch between Sublime Merge and the terminal any time, on the same folder.

### Open a terminal in the project

In File Explorer, right-click inside the `shared-with-daniel` folder →
**Open Git Bash here** (on Windows 11 you may need to click *Show more options* first).

> 💡 **Terminal tips:** You type a command and press Enter. Commands are case-sensitive.
> To paste in Git Bash, use **Shift+Insert** or right-click → Paste. (Ctrl+V doesn't work there.)

### Buttons → commands

| In Sublime Merge | On the command line |
|------------------|---------------------|
| **Pull** button | `git pull` |
| Looking at the *Working Directory* line | `git status` |
| **Stage All** button | `git add .` |
| Typing a message, then **Commit** | `git commit -m "your message"` |
| **Push** button | `git push` |
| Looking at the history | `git log --oneline` (press `q` to quit) |
| *File → Clone Repository* | `git clone https://github.com/guillaumekuc/shared-with-daniel.git` |

### The routine as commands

```bash
git pull                    # 1. get Guillaume's latest changes
# ... edit files ...
git status                  #    (see what changed: red = not staged yet)
git add .                   # 2. stage everything that changed (the "." means "everything")
git status                  #    (now it's green)
git commit -m "what I did"  # 3. snapshot with a note
git push                    # 4. share it
```

**Exercise:** sign the guestbook a second time, using only these commands.
Then look in Sublime Merge: your commit shows up there too.

### Terminal-specific gotchas

**"not a git repository".** You're in the wrong folder. Type `cd ~/shared-with-daniel`
(or reopen Git Bash with the right-click inside the folder).

**Notepad opens by itself after `git pull`.** Git wants a note for combining your work
with Guillaume's. The default text is fine: close Notepad (save if it asks), and Git continues.

**Conflict in the terminal.** The file contains markers like this:

```
<<<<<<< HEAD
your version
=======
Guillaume's version
>>>>>>> ...
```

Fix the text, delete the `<<<<<<<`, `=======` and `>>>>>>>` lines, save, then
`git add .`, `git commit -m "Fix conflict"` and `git push`.
(Or open Sublime Merge, which is usually more comfortable for this.)

---

*Images: official [Sublime Merge documentation](https://www.sublimemerge.com/docs/getting_started).
The interface may have changed a little since, but the buttons have the same names.*
