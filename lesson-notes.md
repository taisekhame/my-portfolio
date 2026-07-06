# Lesson 23 — GitHub: Remote Repos, Push, Pull, Branching & PRs
**Curriculum reference:** Tuesday Week 3

---

## Part A: GitHub

GitHub is a website that hosts Git repositories in the cloud. It adds:
- A web interface to browse your code
- Collaboration tools (pull requests, issues, code review)
- GitHub Pages — free static site hosting
- A public profile showing your work to employers

GitHub is not the only option (GitLab and Bitbucket exist) but it's the industry standard for open source and the most recognised by employers.

---

## Connecting Local to Remote

### Step 1 — Create a repository on GitHub

1. Go to https://github.com and sign in
2. Click the **+** icon → **New repository**
3. Name it (e.g. `my-portfolio`)
4. Set it to **Public** (required for GitHub Pages)
5. Do NOT initialise with a README if you already have a local repo
6. Click **Create repository**

### Step 2 — Link your local repo to GitHub

GitHub will show you the commands. They look like this:

```bash
# Add the remote (named "origin" by convention)
git remote add origin https://github.com/your-username/my-portfolio.git

# Rename local branch to main (if needed)
git branch -M main

# Push your commits to GitHub for the first time
git push -u origin main
```

The `-u` flag sets `origin main` as the default — after this you can just use `git push`.

### Step 3 — Subsequent pushes

```bash
# After making commits locally:
git push
```

### Pulling changes

If you or a collaborator made changes on GitHub directly:

```bash
git pull
```

This fetches and merges the remote changes into your local branch or branches.

---

## Part B: Branching

Branches let you work on a new feature or fix without touching the stable main codebase.

```
main ─────────────────────────────────●────●
                 ↘                  ↗
           feature ──●──●──●──●─────
```

### Essential branch commands

```bash
# List all branches (* marks current)
git branch

# Create a new branch
git branch feature-dark-mode

# Switch to it (modern syntax)
git switch feature-dark-mode

# Create AND switch in one command
git switch -c feature-contact-form

# Old syntax (still works, widely seen)
git checkout -b feature-contact-form

# Merge a branch back into main
git switch main
git merge feature-dark-mode

# Delete a branch after merging
git branch -d feature-dark-mode

# Push a branch to GitHub
git push origin feature-dark-mode
```

### Understanding HEAD

`HEAD` is a pointer to your current position in the commit history — usually the tip of your current branch. When you switch branches, `HEAD` moves.

```bash
# See where HEAD points
git log --oneline --graph --all
```

---

## Part C: Pull Requests (PRs)

A Pull Request is a GitHub feature (not a Git feature) that lets you propose merging one branch into another. It's the primary collaboration mechanism.

### Opening a PR

1. Push your branch to GitHub: `git push origin feature-branch`
2. Go to your repo on GitHub — you'll see a banner: "Compare & pull request"
3. Click it → add a title and description
4. Click **Create pull request**
5. Reviewers can leave comments on specific lines
6. Once approved, click **Merge pull request**

### Why use PRs even when working alone?

- You can review your own changes before merging
- It creates a record of what was changed and why
- GitHub checks (like CSS validators) can run automatically

---

## Part D: Merge Conflicts

A merge conflict happens when two branches change the same part of the same file.

```
<<<<<<< HEAD
.card { background: white; }
=======
.card { background: #f5f5f5; }
>>>>>>> feature-branch
```

To resolve:
1. Open the conflicted file in VS Code
2. VS Code highlights conflicts — choose "Accept Current", "Accept Incoming", or edit manually
3. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Stage and commit the resolution:

```bash
git add style.css
git commit -m "Resolve merge conflict in card background colour"
```

---

## Part E: The .gitignore File

Files listed in `.gitignore` are never tracked by Git — they don't appear in `git status` and are never committed.

```bash
# In your project root, create .gitignore:
.DS_Store
Thumbs.db
node_modules/
.env
*.log
```

GitHub provides templates for common project types at: https://github.com/github/gitignore

---

## The Full Local → Remote Workflow

```bash
# 1. Make changes to your project
# 2. Stage
git add .
# 3. Commit
git commit -m "Descriptive message"
# 4. Push to GitHub
git push
# 5. Verify on github.com
```

---

## Resources

| Resource | Link |
|----------|------|
| GitHub Docs | https://docs.github.com/en |
| Learn Git Branching (visual) | https://learngitbranching.js.org/ |
| GitHub gitignore templates | https://github.com/github/gitignore |
| GitHub Desktop (GUI option) | https://desktop.github.com/ |
