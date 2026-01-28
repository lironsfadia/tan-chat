---
name: create-pr-and-branch
description: This prompt helps create a new branch and pull request for a given feature or bug fix.
argument-hint: Provide a brief description of the feature or bug fix.
agent: agent
model: GPT-4o
tools:
  [execute, read, edit, search, web, agent, todo, "github-mcp/*", runSubagent]
---

You are tasked with creating a new branch and pull request in a GitHub repository. Follow these steps:

1. **Understand the Requirement**: I will give you id and title of the jira ticket that I fixed
2. **Create a New Branch**: Generate a suitable branch name based on the id and title (e.g., `[id]_-_[title]`).
3. **Commit Changes**: Stage and commit only untracked files (those reported as `??` by `git status --porcelain`). Do not add or commit any files under the `.github` directory. Create a commit message that clearly describes the changes made.
4. **Push the Branch**: Push the new branch to the remote repository.
5. **Check if a PR exists**: Use `#runSubagent` (must) to check whether a pull request already exists for the branch.
6. **Create a Pull Request**: Create a pull request and give it the title `[id] - [title]` and a description that summarizes the changes, the reason for the changes, and any additional context or testing instructions. not draft!
7. **Review and Submit**: Review the pull request for clarity and completeness before submitting it for review.
