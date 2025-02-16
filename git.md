# Git Commands

Git is a distributed version control system that allows multiple developers to work on a project simultaneously without overwriting each other's changes. Here are some fundamental Git commands:

## Initializing a Repository
To start a new repository, navigate to your project directory and execute:

```bash
git init
```

## Cloning a Repository
To create a local copy of a remote repository:

```bash
git clone <repository_url>
```

## Checking Repository Status
To view the status of your working directory and staging area:

```bash
git status
```

## Adding Changes
To stage modified or new files:

```bash
git add <file_name>
```

To stage all changes:

```bash
git add .
```

## Committing Changes
To commit staged changes with a message:

```bash
git commit -m "Your commit message"
```

## Viewing Commit History
To see the commit history:

```bash
git log
```

## Pushing Changes
To upload local commits to a remote repository:

```bash
git push origin <branch_name>
```

## Pulling Changes
To fetch and merge changes from a remote repository:

```bash
git pull origin <branch_name>
```

# Branches & Merging

Branches in Git allow you to develop features, fix bugs, or experiment in isolated environments.

## Creating a New Branch
To create and switch to a new branch:

```bash
git checkout -b <new_branch_name>
```

## Switching Branches
To switch to an existing branch:

```bash
git checkout <branch_name>
```

## Merging Branches
To merge a branch into your current branch:

```bash
git merge <branch_name>
```

If there are conflicts, Git will highlight them, and you'll need to resolve them manually.

## Deleting a Branch
To delete a branch that is no longer needed:

```bash
git branch -d <branch_name>
```

# Pull Requests and Solving Conflicts

A pull request (PR) is a way to propose changes to a codebase. It's commonly used in collaborative environments to review and discuss code before merging.

## Creating a Pull Request
1. Push your feature branch to the remote repository:

   ```bash
   git push origin <feature_branch>
   ```

2. Navigate to the repository on GitHub.
3. Click on "Compare & pull request" for your branch.
4. Add a descriptive title and description, then click "Create pull request."

## Resolving Merge Conflicts
Merge conflicts occur when changes in different branches conflict. To resolve them:

1. Fetch the latest changes:

   ```bash
   git fetch origin
   ```

2. Merge the target branch into your feature branch:

   ```bash
   git merge origin/<target_branch>
   ```

3. Git will indicate conflicts in affected files. Open these files to resolve conflicts manually.
4. After resolving, stage the changes:

   ```bash
   git add <file_name>
   ```

5. Continue the merge process:

   ```bash
   git merge --continue
   ```

6. Push the resolved changes:

   ```bash
   git push origin <feature_branch>
   ```

# GitHub Projects: Creating One and Closing Issues with Commit Messages

GitHub Projects offer a flexible way to manage work by organizing issues, pull requests, and notes into a Kanban-style board.

## Creating a GitHub Project
1. **Navigate to the Repository**: Go to the main page of the repository where you want to create the project.
2. **Access Projects**: Click on the "Projects" tab.
3. **Create a New Project**: Click "New project," provide a name and description, choose a template if desired, and click "Create project."

## Closing Issues with Commit Messages
You can automatically close issues by including specific keywords in your commit messages, followed by the issue number.

**Syntax:**

```
Fixes #issue_number
```

**Example:**

```bash
git commit -m "Fix authentication error in OAuth flow. Fixes #42"
```

Upon pushing this commit to the default branch (or the branch specified in the repository's settings), issue number 42 will be automatically closed.

# Structure of a Good Commit Message

A well-structured commit message enhances project maintainability and collaboration. A common convention follows this format:

```
type(scope): subject

body

footer
```

### Type
Indicates the nature of the change. Common types include:
- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation changes
- `style`: Code style changes
- `refactor`: Code refactoring without changing functionality
- `test`: Adding or modifying tests
- `chore`: Maintenance tasks

### Scope
Specifies the section of the codebase affected (e.g., `auth`, `api`, `ui`).

### Subject
A brief description of the change.

### Body (Optional)
Detailed explanation of the change, reasons, and any additional context.

### Footer (Optional)
References to issues or pull requests affected, using keywords to automatically close issues.

**Example:**

```
fix(auth): handle token expiration

Ensure the application correctly refreshes tokens when they expire,
preventing users from being logged out unexpectedly.

Closes #108
```

# GitHub Organisations

## Transferring a Repository to a GitHub Organization

### Prerequisites
- **Administrative Access:** Ensure you have admin rights to the repository you intend to transfer.
- **Organization Permissions:** You must have permission to create repositories in the target organization.
- **Repository Name Conflict:** The target organization should not have an existing repository with the same name.

### Steps to Transfer
1. **Navigate to Repository Settings:**
    - Go to the main page of your repository on GitHub.
    - Click on the "Settings" tab.
2. **Initiate Transfer:**
    - Scroll down to the "Danger Zone" section.
    - Click on "Transfer".
3. **Confirm Transfer Details:**
    - Enter the name of the repository to confirm.
    - Specify the new owner's username or organization name.
    - Click "I understand, transfer this repository".

## Accessing Private Repositories Using a Personal Access Token (PAT)

### Creating a Personal Access Token
1. **Access Developer Settings:**
    - Log in to your GitHub account.
    - Click on your profile picture in the top-right corner and select "Settings".
    - In the left sidebar, click on "Developer settings".
2. **Generate New Token:**
    - Click on "Personal access tokens".
    - Click "Generate new token".
    - Provide a descriptive name for the token.
    - Select the necessary scopes (e.g., `repo`).
    - Click "Generate token".
3. **Save the Token:**
    - Copy the generated token immediately.
    - Store it securely; you won't be able to view it again.

### Updating Remote URL with PAT

```bash
git remote set-url origin https://<username>:<PAT>@github.com/<organization>/<repository>.git
```

Verify the change:
```bash
git remote -v
```

**Security Note:** Avoid embedding PATs in remote URLs; use credential managers or SSH authentication for better security.
