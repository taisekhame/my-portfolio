# Lesson 23 — Classwork & Assignments

---

## In-Class Work & Assignment

### Task 1 — Push Your Portfolio to GitHub (10 mins)

Work through this sequence on your own machine:

```bash
# 1. Make sure your portfolio has at least 5 commits
git log --oneline    # should show 5+ commits

# 2. Go to github.com → New Repository
#    Name: my-portfolio   Visibility: Public   No README

# 3. Connect and push
git remote add origin https://github.com/YOUR-USERNAME/my-portfolio.git
git branch -M main
git push -u origin main

# 4. Visit github.com/YOUR-USERNAME/my-portfolio
#    You should see your files in the browser!
```

Raise your hand when you can see your code on GitHub.

### Task 2 — Create and Merge a Branch (5 mins)

```bash
# Create a feature branch
git switch -c feature-readme

# Create a README.md file
echo "# My Portfolio" > README.md
echo "A personal portfolio built with HTML and CSS." >> README.md

# Stage, commit, push the branch
git add README.md
git commit -m "Add project README"
git push origin feature-readme

# On GitHub: open a Pull Request for feature-readme → main
# Merge it via the GitHub interface

# Back in terminal: update your local main
git switch main
git pull
git log --oneline    # README commit should now be on main
```

---

## Assignment (Complete Before Next Lesson)

### Assignment 23 — Portfolio on GitHub with Clean History

**Step 1 — Verify your remote**
```bash
git remote -v    # should show origin pointing to github.com
```

**Step 2 — Ensure clean commit history**

Run `git log --oneline`. Your history should tell a story. Example of a good history:
```
a3f1c2d Fix mobile nav overflow on small screens
9b2e4a1 Add contact form with validation styling
c7d8f3e Add profile image and update About section
4e9a1b2 Add CSS animations and transition polish
2f3d5c8 Add project cards with image hover effects
8a1c4d7 Add responsive breakpoints for tablet and mobile
1b5e2a3 Add CSS variables and BEM naming
0c7f9d2 Initial commit: portfolio HTML and CSS structure
```

**Step 3 — Add a README.md to your repository**

Create `README.md` in your project root:

```markdown
# [Your Name] — Portfolio

A personal portfolio website built with HTML5 and CSS3.

## Live Demo
[View on GitHub Pages](https://your-username.github.io/my-portfolio)

## Features
- Responsive design (mobile, tablet, desktop)
- CSS Grid and Flexbox layouts
- CSS custom properties for theming
- @keyframes entrance animations
- Mobile hamburger navigation
- Contact form

## Technologies
- HTML5 (semantic markup)
- CSS3 (custom properties, Grid, Flexbox, animations)
- Google Fonts
- Git & GitHub

## Local Development
Clone the repository and open `index.html` in a browser.
No build tools required.
```

```bash
git add README.md
git commit -m "Add project README with live demo link"
git push
```

**Requirements:**
- Repo is public on GitHub
- `git log --oneline` shows at least 5 meaningful commits
- README.md is present and describes the project
- `.gitignore` is present

---

## Reflection Questions

1. What is the difference between `git fetch` and `git pull`?
2. You are working on a `feature-dark-mode` branch. A colleague pushes a bug fix to `main`. How do you get their fix into your branch without merging your branch into main?
3. A merge conflict shows `<<<<<<< HEAD` markers. What does HEAD refer to in this context?
