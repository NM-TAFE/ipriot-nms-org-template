# Git Onboarding Guide
>
> North Metro Software Pty Ltd

Welcome to North Metro Software! This guide outlines our Git workflow and branch naming conventions, designed to ensure smooth collaboration and maintain the integrity of our codebase. Our practices are based on GitHub Flow and conventional commits, with some adaptations to suit our enterprise environment.

## 1. Repository Structure

We follow a simplified GitHub Flow model with a single long-lived branch:

- `main`: The primary branch containing production-ready code

### Repository Configuration

Ensure all repositories are configured with the default branch set to `main` and your employee id (under student id) as your user.name and company (tafe.wa.edu.au) email as user.email.

Check in with LF and checkout with local line endings (CRLF on windows).

The following commands will set your user.name and user.email:

```bash
git config --global user.name "20012345"
git config --global user.email "20012345@tafe.wa.edu.au"
```

Ensure default branch is set to `main`:

```bash
git config --global init.defaultBranch main
```

Set line endings to LF on commit and auto on checkout:

```bash
git config --global core.autocrlf true
```

Note: if working on a project that has multiple developers on different operating systems, it is recommended to also add a `.gitattributes` file to the repository to ensure line endings are consistent across all platforms.

```bash
# .gitattributes
# Set the default behavior, in case people don't have core.autocrlf set.
* text=auto
```

## 2. Branch Naming Conventions

Format: `<type>/<brief-description>`

Types:

- `feature`: For new features or enhancements
- `fix`: For bug fixes
- `hotfix`: For critical bugs in production
- `docs`: For documentation changes
- `refactor`: For code refactoring
- `test`: For adding or modifying tests
- `chore`: For routine tasks, maintenance, or tooling changes

Examples:

- `feature/add-user-authentication`
- `fix/resolve-login-error`
- `hotfix/patch-security-vulnerability`

## 3. Commit Messages

We use a modified version of conventional commits:

Format: `<type>(<scope>): <description>`

Example: `feat(auth): implement password reset functionality`

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`, `perf`

The scope is optional and should indicate the module or component affected. 

See [Udacity Commit Message Style Guide](https://udacity.github.io/git-styleguide/) for more details.

## 4. Standard workflow

Follow these steps for each task or feature you work on:

1. **Start with an Up-to-Date Main Branch**

   ```bash
   git switch main
   git pull origin main
   ```

2. **Create a New Branch**
   - For planned work (created by tech lead during sprint planning):

     ```bash
     git fetch origin
     git switch <branch-name>
     ```

   - For unplanned work:

     ```bash
     git switch -c <type>/<brief-description>
     ```

   - Example: `git switch -c feature/add-login-page`

3. **Work on Your Branch**
   - Make changes to your code
   - Stage your changes:

     ```bash
     git add <file-name>
     ```

   - Or stage all changes:

     ```bash
     git add .
     ```

   - Commit your changes:

     ```bash
     git commit -m "<type>(<scope>): <description>"
     ```

   - Example: `git commit -m "feat(auth): implement login form"`

4. **Push Your Branch**

   ```bash
   git push -u origin <branch-name>
   ```

5. **Keep Your Branch Updated**

   ```bash
   git switch <branch-name>
   git pull origin main
   ```

   - If there are conflicts, resolve them in your code editor

6. **Create a Pull Request**
   - Go to the repository on GitHub
   - Click "Pull requests" > "New pull request"
   - Select your branch
   - Fill in the PR template
   - Assign reviewers and add labels

7. **Address Review Comments**
   - Make necessary changes in your local branch
   - Commit and push the changes

   ```bash
   git commit -m "fix(auth): address review comments"
   git push origin <branch-name>
   ```

8. **Update Your PR if Needed**
   - If main has been updated, rebase your branch:

     ```bash
     git switch main
     git pull origin main
     git switch <branch-name>
     git rebase main
     ```

   - If there are conflicts, resolve them and then:

     ```bash
     git add .
     git rebase --continue
     git push --force-with-lease origin <branch-name>
     ```

9. **Merge Your PR**
   - Once approved, click "Squash and merge" on GitHub
   - Confirm the squash commit message
   - Delete the branch on GitHub when prompted

10. **Clean Up Locally**

    ```bash
    git switch main
    git pull origin main
    git branch -d <branch-name>
    ```

11. **Celebrate!** 🎉

🤔 Remember:

- Commit often with clear, conventional commit messages
- Push your branch regularly to back up your work
- Communicate with your team about significant changes or blockers
- Use GitHub issues and PR comments for discussions

## 5. Handling Merge Conflicts

If you encounter merge conflicts:

1. **Identify the Conflicting Files**

   ```bash
   git status
   ```

2. **Open the Conflicting Files**
   - Look for conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
   - Manually edit the files to resolve conflicts

3. **Stage the Resolved Files**

   ```bash
   git add <resolved-file>
   ```

4. **Complete the Merge or Rebase**
   - For a merge:

     ```bash
     git commit
     ```

   - For a rebase:

     ```bash
     git rebase --continue
     ```

5. **Push Your Changes**

> **Note:** Before pushing changes, ensure your branch reflects the latest changes by first fetching main and then rebasing or merging. Generally, we prefer a rebase workflow, but if working on a shared branch, ensure good team communication. 

   ```bash
   git push origin <branch-name>
   ```


## 5. Pull Requests

- Use the PR template provided in the repository
- Link the relevant issue(s) in the PR description
- Ensure all CI checks pass before requesting review


## 6. Code Review Process

- Reviewers should respond within 1 business day
- Use "Request changes" for blocking issues, "Comment" for suggestions
- Final approval should come from a senior developer or team lead

## 7. Release Process

1. We practice continuous deployment to staging environments
2. Release candidates are tagged from `main` as `rc-<version>`
3. After final testing, create a release tag `v<major>.<minor>.<patch>`
4. Our CI/CD pipeline automates deployment based on these tags

## 8. Git Best Practices

- Keep branches short-lived (aim for < 1 week)
- Rebase on `main` before creating a PR to resolve conflicts
- Write clear, concise commit messages
- Squash commits when merging to maintain a clean history

## 9. GitHub and Automation

- We use GitHub Actions for CI/CD
- Branch protection rules enforce our review process
- Automated linting, testing, and security scans run on all PRs
- We use GitHub Issues for task tracking and project management

## 10. Support and Resources

- For Git or GitHub issues, contact the DevOps team at <devops@northmetrosoftware-is-not-real.com.au>
- Refer to our internal wiki for detailed Git tutorials and troubleshooting guides
- Monthly "Git & GitHub Best Practices" workshops are available for all developers

Remember, these guidelines are designed to improve our collective productivity and code quality. If you have any questions or suggestions for improvement, please don't hesitate to discuss with your team lead or manager.

Happy coding!
