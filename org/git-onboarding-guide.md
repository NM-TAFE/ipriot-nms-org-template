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
git config --global core.autocrlf tru   e
```

Note: if working on a project that has multilple developers on different operating systems, it is recommended to also add a `.gitattributes` file to the repository to ensure line endings are consistent across all platforms.

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

The scope is optional and should indicate the module or component affected. See [commit message guidelines](commit-message-guidelines.md) for more details.

## 4. Workflow

1. Create a new branch from `main` for your work
2. Commit changes to your branch, pushing regularly
3. Open a Pull Request (PR) to merge your branch into `main`
4. Ensure all automated checks pass and address review comments
5. After approval, merge using "Squash and merge"
6. Delete your branch after merging

## 5. Pull Requests

- Use the PR template provided in the repository
- Link the relevant issue(s) in the PR description
- Ensure all CI checks pass before requesting review
- Obtain at least two approvals before merging

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

- For Git or GitHub issues, contact the DevOps team at <devops@northmetrosoftware.com>
- Refer to our internal wiki for detailed Git tutorials and troubleshooting guides
- Monthly "Git & GitHub Best Practices" workshops are available for all developers

Remember, these guidelines are designed to improve our collective productivity and code quality. If you have any questions or suggestions for improvement, please don't hesitate to discuss with your team lead or manager.

Happy coding!
