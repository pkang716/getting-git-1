# Assignment 01 – Say Hello to `.git` 🚀
*Estimated time — 30‑40 minutes*

Welcome to Git! In this mini‑lab you will

1. Make your **first commit**  
2. Peek inside the mysterious **`.git` folder**  
3. See how Git stores your work *under the hood*

No fancy branching, no GitHub magic yet—just the essentials.

---

## ✍️ What you’ll deliver
1. A screenshot **or** copy‑paste of the commands you ran **plus** their output  
2. A short reflection (2‑3 sentences) answering:

> “One thing that surprised me about what’s inside the `.git` folder was …”

Commit that reflection into the same repo before pushing (steps at the end).

---

## 🛠 Before you start

| Tool | macOS / Linux | Windows |
|------|---------------|---------|
| **Git** | `brew install git` *(or use your distro’s package manager)* | Install **Git for Windows** — includes **Git Bash** <https://git-scm.com> |
| **tree** *(nice to have)* | `brew install tree` • `sudo apt install tree` | `choco install tree` **or** use `dir /s` |
| **Terminal** | Any shell | **Git Bash** (preferred) • PowerShell/CMD also work |

> **Note for PowerShell / CMD**   
> `echo "text" > file.txt` ➜ use `'text' > file.txt` (quotes single).  
> Directory listings: `tree` ➜ `dir /s`.  
> Viewing files: `cat` ➜ `type`.

---

## 🚶‍♂️ Part A – Create & Commit (≈10 min)

```bash
# 1  Make a playground folder and jump in
mkdir first-git-lab && cd first-git-lab           # Windows CMD: md first-git-lab & cd first-git-lab

# 2  Turn the folder into a Git repo
git init                                          # creates the hidden .git folder

# 3  Add a file
echo "Hello Git!" > hello.txt                     # PowerShell: 'Hello Git!' > hello.txt

# 4  Stage & commit
git add hello.txt
git commit -m "Initial commit – add greeting"
```

Quick check:

```bash
git log --oneline    # you should see *one* commit
```

---

## 🔍 Part B – Peek Inside `.git` (≈15 min)

| Goal | macOS / Linux | Windows |
|------|---------------|---------|
| **List contents** | `tree .git` | `tree .git` **or** `dir /s .git` |
| **Identify object type** | `git cat-file -t <HASH>` | same |
| **Print object** | `git cat-file -p <HASH>` | same |
| **View HEAD pointers** | `cat .git/HEAD`<br>`cat .git/refs/heads/main` | `type .git\HEAD`<br>`type .git\refs\heads\main` |

### Steps

1. Run the *listing* command above.  
2. In `.git/objects/` you’ll see two‑character folders. Inside each is a file whose name completes a 40‑char SHA‑1 hash. Pick each and run `git cat-file` to discover:  
   * **blob** → holds the text “Hello Git!”  
   * **tree** → lists `hello.txt`  
   * **commit** → stores author, date, message, plus a pointer to the tree  
3. Read `.git/HEAD` and the file it points at.  
   *HEAD is just a text pointer that says “you’re on branch *main* and here’s its latest commit.”*

---

## 💬 Part C – Reflect (≈5 min)

Create a file called `REFLECTION.md` containing your 2‑3 sentence answer.

```bash
git add REFLECTION.md
git commit -m "Add reflection for Assignment 01"
```

---

## 🚀 Part D – Push to GitHub (first‑time setup)

1. On GitHub create an **empty** repo named `getting-git` (no README).  
2. Back in the terminal:

```bash
git remote add origin https://github.com/<your‑user>/getting-git.git
git branch -M main          # rename master → main if needed
git push -u origin main     # -u stores the upstream link for next time
```

You’ve now pushed both your code **and** reflection to GitHub—nice work! 🎉

---

## ⭐ Extra credit (optional)

```bash
git status
git show
```

Write one interesting flag or line of output you didn’t know about.

---

### Cheatsheet for Windows PowerShell / CMD

| Bash cmd | PowerShell / CMD |
|----------|------------------|
| `echo "hi" > file` | `'hi' > file` |
| `cat file` | `type file` |
| `tree` | `dir /s` |
| Forward‑slashes `/` in paths | Use back‑slashes `\` |

*(Using **Git Bash** avoids nearly all of these quirks.)*
