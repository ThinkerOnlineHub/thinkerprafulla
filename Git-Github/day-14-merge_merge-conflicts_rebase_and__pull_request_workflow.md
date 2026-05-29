# Git & GitHub Real-World Practice Lab

## Topic: Merge, Merge Conflicts, Rebase & Pull Request Workflow


---

# 🎯 Goal

In this lab, we practiced:

* Creating branches
* Working on multiple branches
* Creating merge conflicts intentionally
* Resolving conflicts manually
* Understanding merge workflow
* Understanding Git history visualization
* Push branches to GitHub
* Create Pull Request workflow understanding

---

# 📁 Repository Path

```bash
cd ~/Movies/"Thinker TechSutra Marathi"/"DevOps-Git Learning"/Git-Github
```

---

# 📂 Current Repository Structure

```text
DevOps-Git Learning/
│
├── Dev Ops Content Master Prompt & Workflow.pdf
├── dev_ops_content_master_prompt_workflow.md
├── techsutra_key.pem
└── Git-Github/
    ├── day-11-git-basics-foundation.md
    ├── day-12-remote_repo_github-connection.md
    ├── day-13-branching.md
    ├── GitHub-SSH-Setup.md
    ├── screenshots/
    └── merge-practice.txt
```

---

# ⚠️ Important Security Note

```text
Never upload:
.pem
private keys
SSH secret files
```

Always add them into:

```bash
.gitignore
```

---

# ✅ STEP 1 — Verify Repository Status

## Command

```bash
git status
```

## Output

```bash
On branch main
Your branch is up to date with 'origin/main'.

nothing to commit, working tree clean
```

---

# ✅ STEP 2 — Check Existing Files

## Command

```bash
ls
```

## Output

```bash
day-11-git-basics-foundation.md
day-12-remote_repo_github-connection.md
day-13-branching.md
GitHub-SSH-Setup.md
screenshots
```

---

# ✅ STEP 3 — Create Feature Branch

## Command

```bash
git checkout -b feature-login
```

## Output

```bash
Switched to a new branch 'feature-login'
```

---

# ✅ STEP 4 — Verify Branches

## Command

```bash
git branch
```

## Output

```bash
* feature-login
  feature/day-13-branching
  main
```

---

# ✅ STEP 5 — Create Merge Practice File

## Command

```bash
nano merge-practice.txt
```

## Added Content

```text
Application Name: Thinker PlatformOps

Version: 1.0
Environment: Development
```

---

# ✅ STEP 6 — Add & Commit Changes

## Wrong Command Attempt

```bash
git add
```

## Error

```bash
Nothing specified, nothing added.
hint: Maybe you wanted to say 'git add .'?
```

---

## Correct Command

```bash
git add .
```

## Commit

```bash
git commit -m "Added merge practice file"
```

## Output

```bash
[feature-login 6b8f1d4] Added merge practice file
```

---

# ✅ STEP 7 — Switch Back To Main Branch

## Command

```bash
git checkout main
```

## Output

```bash
Switched to branch 'main'
```

---

# ✅ STEP 8 — Modify Same File On Main Branch

## Command

```bash
nano merge-practice.txt
```

## Updated Content

```text
Application Name: Thinker PlatformOps

Version: 2.0
Environment: Production
```

---

# ✅ STEP 9 — Commit Main Branch Changes

## Command

```bash
git add .
```

```bash
git commit -m "Updated application version on main"
```

## Output

```bash
[main b6d2f2f] Updated application version on main
```

---

# ✅ STEP 10 — Merge Feature Branch Into Main

## Command

```bash
git merge feature-login
```

## Output

```bash
CONFLICT (add/add): Merge conflict in merge-practice.txt
Automatic merge failed; fix conflicts and then commit the result.
```

---

# 🔥 REAL-WORLD MERGE CONFLICT CREATED

This is exactly what happens in real DevOps teams when:

* Two developers edit the same file
* Both changes are different
* Git cannot decide automatically

---

# ✅ STEP 11 — View Conflict File

## Command

```bash
cat merge-practice.txt
```

## Output

```text
Application Name: Thinker PlatformOps

<<<<<<< HEAD
Version: 2.0
Environment: Production
=======
Version: 1.0
Environment: Development
>>>>>>> feature-login
```

---

# 🧠 Understanding Conflict Markers

| Marker                  | Meaning                 |
| ----------------------- | ----------------------- |
| `<<<<<<< HEAD`          | Current branch changes  |
| `=======`               | Separation line         |
| `>>>>>>> feature-login` | Incoming branch changes |

---

# ✅ STEP 12 — Resolve Conflict Manually

## Command

```bash
nano merge-practice.txt
```

## Final Resolved Content

```text
Application Name: Thinker PlatformOps

Version: 2.0
Environment: Production

Previous Version:
Version: 1.0
Environment: Development
```

---

# ✅ STEP 13 — Finalize Conflict Resolution

## Command

```bash
git add merge-practice.txt
```

```bash
git commit -m "Resolved merge conflict manually"
```

## Output

```bash
[main 35cdba8] Resolved merge conflict manually
```

---

# ✅ STEP 14 — Visualize Git History Graph

## Wrong Command Attempt

```bash
git log --online --graph --all
```

## Error

```bash
fatal: unrecognized argument: --online
```

---

## Correct Command

```bash
git log --oneline --graph --all
```

## Output

```bash
* 35cdba8 (HEAD -> main) Resolved merge conflict manually
|\
| * 6b8f1d4 (feature-login) Added merge practice file
* | b6d2f2f Updated application version on main
|/
```

---

# 🧠 Understanding Git Graph

| Symbol  | Meaning    |             |
| ------- | ---------- | ----------- |
| `*`     | Commit     |             |
| `       | `          | Branch line |
| `\` `/` | Merge path |             |

---

# ✅ STEP 15 — Push Main Branch To GitHub

## Command

```bash
git push origin main
```

## Output

```bash
To github.com:ThinkerOnlineHub/git-github-mastery.git
aadaccf..35cdba8 main -> main
```

---

# ✅ STEP 16 — Push Feature Branch

## Command

```bash
git push origin feature-login
```

## Output

```bash
[new branch] feature-login -> feature-login
```

GitHub also suggested PR URL:

```text
Create a pull request for 'feature-login'
```

---

# 🔥 Pull Request Concept

In real companies:

```text
Developer →
Feature Branch →
Push →
Pull Request →
Code Review →
Merge →
Production
```

---

# ✅ STEP 17 — Additional Branch Practice

## Wrong Commands Practiced

```bash
git checkout -b main
```

## Error

```bash
fatal: a branch named 'main' already exists
```

---

```bash
git checkout -b feature-login
```

## Error

```bash
fatal: a branch named 'feature-login' already exists
```

---

# 🧠 Learning

Git prevents duplicate branch creation.

---

# ✅ STEP 18 — Verify Final Branches

## Command

```bash
git branch
```

## Output

```bash
branch-name
feature-login
feature/day-13-branching
main
```

---

# ✅ STEP 19 — Final Repository Status

## Command

```bash
git status
```

## Output

```bash
nothing to commit, working tree clean
```

---

# ✅ STEP 20 — Final Git Graph

## Command

```bash
git log --oneline --graph --all
```

## Important Commits

```bash
35cdba8 Resolved merge conflict manually
6b8f1d4 Added merge practice file
b6d2f2f Updated application version on main
aadaccf Reorganize DevOps-Git Learning repository structure
```

---

# 🧠 Key Concepts Learned

| Topic                      | Learned |
| -------------------------- | ------- |
| Branching                  | ✅       |
| Feature workflow           | ✅       |
| Merge conflict             | ✅       |
| Manual conflict resolution | ✅       |
| Git graph visualization    | ✅       |
| Git history tracking       | ✅       |
| Git push                   | ✅       |
| Feature branch push        | ✅       |
| Pull Request workflow      | ✅       |

---

# 🔥 Real DevOps Industry Workflow

```text
Developer creates feature branch
        ↓
Makes code changes
        ↓
Commits changes
        ↓
Pushes branch to GitHub
        ↓
Creates Pull Request
        ↓
Team reviews code
        ↓
Conflicts resolved if needed
        ↓
Merged into main branch
        ↓
CI/CD deployment starts
```

---

# 📘 Commands Practiced

```bash
git status
git branch
git checkout
git checkout -b
git add .
git commit -m
git merge
git log --oneline --graph --all
git push origin main
git push origin feature-login
```

---

# ✅ Final Result

Successfully completed:

* Real-world Git branching workflow
* Merge conflict handling
* Conflict resolution
* Git graph visualization
* Feature branch workflow
* Pull Request understanding
* Industry-level Git collaboration practice

🚀 Git & GitHub hands-on practice completed successfully.
