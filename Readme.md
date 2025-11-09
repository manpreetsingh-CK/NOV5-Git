


### 1. Create a Repository on GitHub

I created a new repository on GitHub named **NOV5-Git**.

---

### 2. Clone the Repository

I cloned the repo from GitHub to my local system using:

```bash
git clone https://github.com/manpreetsingh-CK/NOV5-Git.git
```

This created a local folder where I can make changes.

---

### 3. Create and Commit a File in Main Branch

Inside the repo folder, I made a new file `test.txt` and committed it:

```bash
echo "This is a test file" > test.txt
git add test.txt
git commit -m "Added test.txt in main branch"
```

---

### 4. Create Two Branches

I created two new branches from main:

```bash
git branch f1
git branch f2
```

---

### 5. Make Changes in Each Branch

Switched to branch **f1**:

```bash
git checkout f1
echo "Change from f1 branch" >> test.txt
git add .
git commit -m "Updated file from f1"
```

Then switched to **f2**:

```bash
git checkout f2
echo "Change from f2 branch" >> test.txt
git add .
git commit -m "Updated file from f2"
```

---

### 6. Resolve a Merge Conflict

When I tried merging `f1` into `f2`:

```bash
git merge f1
```

It showed a **merge conflict** in `test.txt`.
The file looked like this:

```
<<<<<<< HEAD
Change from f2 branch
=======
Change from f1 branch
>>>>>>> f1
```

I edited it manually to keep both changes, then committed:

```bash
git add test.txt
git commit -m "Resolved merge conflict between f1 and f2"
```

Finally, I pushed the branch:

```bash
git push origin f2
```

---

### 7. Show How Divergence Occurs in a Branch

Divergence happens when two branches move ahead separately.

Example:

```bash
# On f1
echo "new change from f1" >> test.txt
git add .
git commit -m "commit from f1"

# On f2
git checkout f2
echo "new change from f2" >> test.txt
git add .
git commit -m "commit from f2"
```

Now both `f1` and `f2` have different commits, so they’ve diverged.

---

### 8. Difference Between `git init` and `git clone`

* `git init` → Starts a brand new local git repo from scratch.
* `git clone` → Copies an existing remote repo (like from GitHub) to your system.

Example:

```bash
git init myproject     # create new repo
git clone <url>        # copy an existing one
```

---

### 9. Difference Between `git branch` and `git checkout`

* `git branch` → Used to list or create branches.
* `git checkout` → Used to switch between branches.

Example:

```bash
git branch f1
git checkout f1
```

---

### 10. Difference Between `git fetch` and `git pull`

* `git fetch` only downloads new data from remote but doesn’t change your working files.
* `git pull` does fetch + merge automatically into your current branch.

Example:

```bash
git fetch origin
git pull origin main
```

---

### 11. How to Squash Commits

If I have multiple small commits and want to combine them into one clean commit:

```bash
git rebase -i HEAD~3
```

Then change `pick` to `squash` for the commits I want to combine, save, and edit the final message.

Example:

```
pick a1b2 First change
squash b2c3 Second change
squash c3d4 Third change
```

Then save and write one final message like:

```
Updated feature in one clean commit
```

Push it using:

```bash
git push origin branch-name --force
```

---

### 12. Difference Between `git reset` and `git revert`

* `git reset` moves your branch pointer to an earlier commit (it can remove commits).
* `git revert` makes a new commit that undoes the changes of a specific commit.

| Command                   | What it Does            | Safe for Shared Repo |
| ------------------------- | ----------------------- | -------------------- |
| `git reset --hard HEAD~1` | Deletes last commit     | No                   |
| `git revert <commit-id>`  | Creates new undo commit | Yes                  |

---

### 13. Delete Branch from Local and Remote

To delete a branch locally:

```bash
git branch -d branch_name
```

If it’s not merged yet:

```bash
git branch -D branch_name
```

To delete from remote:

```bash
git push origin --delete branch_name
```

Example:

```bash
git branch -d f1
git push origin --delete f1
```


