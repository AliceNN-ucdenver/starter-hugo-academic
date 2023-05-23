---
title: GitHub Introduction
summary: A beginner's guide to GitHub
authors: []
tags: []
categories: []
date: '2023-05-22T00:00:00Z'
slides:
  theme: black
  highlight_style: dracula
---

# Introduction to GitHub

[GitHub](https://github.com/) | [Documentation](https://docs.github.com/en)

---

## What is GitHub?

- A platform for version control and collaboration
- It allows you and others to work on projects from anywhere

---

## Setting Up GitHub

1. Go to [GitHub.com](https://github.com/)
2. Click on `Sign Up`
3. Fill in your details and click `Create account`

---

## Creating a New Repository

1. After logging in, click on `New repository`
2. Name your repository
3. Choose to make the repository `Public` or `Private`
4. Make sure the default branch name is `main`
5. Click `Create repository`

---

## Cloning a Repository

1. Navigate to the main page of the repository
2. Click `Code`
3. To clone the repository using HTTPS, under "Clone with HTTPS", click the clipboard icon
4. Open Git Bash
5. Change the current working directory to the location where you want the cloned directory
6. Type `git clone`, and then paste the URL you copied earlier
7. Press `Enter` to create your local clone

---

## Making Changes

1. Navigate to the file in your repository that you want to change
2. Click the pencil icon in the upper right corner of the file view to edit
3. Make and commit your changes

---

## Creating a .gitignore File

1. In your repository, create a new file named `.gitignore`
2. For a Node.js project, you might include the following in your `.gitignore`:

```txt
node_modules/
npm-debug.log
.DS_Store
.env
```

---

## About .env and .gitignore

- `.env` files usually contain sensitive information like API keys and should not be tracked in Git
- Including `.env` in your `.gitignore` ensures it won't be committed to your GitHub repository
- Instead, provide a `.env.example` file with the required keys and dummy values to guide others

---

## Pushing Changes

1. Open a terminal
2. Navigate to your repository directory
3. Type `git add .` to add all changes
4. Type `git commit -m "Your message"` to commit changes
5. Type `git push` to push changes to GitHub

---

## Pulling Changes

1. Open a terminal
2. Navigate to your repository directory
3. Type `git pull` to update your local repository with the latest changes

---

## Issues

Issues are a great way to keep track of tasks, enhancements, and bugs for your projects

1. Navigate to the main page of the repository
2. Click `Issues`
3. Click `New issue`
4. Create a title and write a description for your issue
5. Click `Submit new issue`

---

## Pull Requests

Pull requests let you tell others about changes you've pushed to a branch in a repository on GitHub

1. Navigate to the main page of the repository
2. Click `Pull requests`
3. Click `New pull request`
4. Select the branch you made changes to and the branch you want to merge changes

into
5. Review your changes and click `Create pull request`

---

# Questions?

[Ask](https://github.community/)
[Documentation](https://docs.github.com/en)