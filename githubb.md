
### 1. **Branching Strategy:**

When working on a backend project with multiple developers, it's important to have a clear branching strategy. Here’s a common strategy:

- **Main branch (usually called `main` or `master`)**:  
  This is the production-ready branch. Only stable, tested, and reviewed code should be merged here. Code in `main` should always be deployable.

- **Develop branch**:  
  This is where all the development work is merged. Developers can push their changes to the `develop` branch after completing features, bug fixes, or improvements. The `develop` branch may be used for staging or pre-production deployments.

- **Feature branches**:  
  Developers create feature branches off of the `develop` branch. These are typically named based on the feature being developed, such as `feature/login-api`, `feature/user-authentication`, or `feature/order-service`.  
  Once the feature is complete, the developer opens a pull request (PR) to merge it back into `develop`.

- **Bugfix branches**:  
  Similar to feature branches, but they are specifically for bug fixes. Naming might follow the convention `bugfix/<issue-number>`, such as `bugfix/fix-login-issue`. Bug fixes are merged into `develop` or sometimes directly into `main` if they need to be deployed immediately.

- **Release branches**:  
  When preparing for a new release, you can create a `release` branch (e.g., `release/1.2.0`). This branch is used for final testing, bug fixes, and tweaks before merging into `main` for deployment.

- **Hotfix branches**:  
  These are for urgent fixes in production. If a critical bug is found in the `main` branch, you can create a hotfix branch, such as `hotfix/fix-crash-issue`, to patch the issue quickly, and then merge it back into both `main` and `develop`.

---

### 2. **Feature Development and Collaboration:**

When collaborating with other developers, the process usually follows these steps:

- **Pull the latest changes from the main branch**:  
  Before you start working on a new feature, always pull the latest changes from the main branch (`git pull origin main`) and merge them into your local branch. This ensures you're working on the most recent code and reduces the chances of conflicts later.

- **Create a feature branch**:  
  Always create a new branch for your feature off of `develop` (or `main`, depending on the workflow). For example:  
  `git checkout -b feature/user-authentication`

- **Regular commits and pushing**:  
  As you work on the feature, commit frequently with descriptive messages, and push your changes to the remote branch regularly so others can see your progress.

- **Review and testing**:  
  Before merging your feature branch into `develop`, ensure that you have written unit tests, integration tests, and that your code is well-reviewed. GitHub allows you to set up review processes and integrate continuous integration (CI) tools to automate testing.

- **Open a Pull Request (PR)**:  
  Once your feature is ready, open a pull request to merge it into the `develop` branch. Add a description of the changes and ask teammates to review it. The review process helps catch bugs or issues and ensures consistency with the codebase.

---

### 3. **Conflict Resolution:**

Merge conflicts occur when multiple developers have modified the same part of a file, and Git cannot automatically decide which changes should be kept.

Here's how to resolve conflicts:

- **Identify the conflict**:  
  When you try to merge a branch, Git will notify you of any conflicts. It will mark the conflicted sections of the files in your working directory.

- **Open the conflicted file(s)**:  
  Git will highlight the conflicting parts using markers like:
  ```bash
  <<<<<<< HEAD
  // your changes
  =======
  // changes from the other branch
  >>>>>>> feature-branch
  ```
  You will need to manually edit the file to choose which version to keep (or combine the changes, if needed). After editing, delete the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
ref : https://www.atlassian.com/git/tutorials/using-branches/merge-conflicts

- **Test the changes**:  
  After resolving the conflict, run your tests to make sure everything is still working properly.

- **Commit the resolved file(s)**:  
  Once you’ve resolved the conflicts, stage the changes (`git add <file>`) and commit them (`git commit`). If you’re using GitHub, the PR will show the conflict as resolved, and you can merge it.

- **Communicate with your team**:  
  If you’re unsure about which changes to keep or how to resolve a conflict, communicate with the developer who made the changes. Sometimes, a discussion or pair programming session is needed to resolve the issue properly.




  PR VS PULL REQUEST 

  ### The Relationship Between Pull Requests (PRs) and Pulls

In Git, **pulls** and **pull requests (PRs)** are both essential to collaborative workflows, but they serve distinct purposes:

---

### **Pull: Synchronizing Code**
A **pull** refers to fetching changes from a remote repository and merging them into your local branch. It ensures your local branch is up-to-date with the remote repository. 

#### **Steps for Pulling Changes:**
1. **Fetch and merge changes from a remote branch:**
   ```bash
   git pull origin main
   ```
   - `git pull` combines `git fetch` (downloads updates) and `git merge` (integrates changes into your branch).
   - This keeps your local branch synchronized with the latest changes from the remote repository.

2. **Rebase instead of merge (optional):**
   If your workflow prefers a linear commit history:
   ```bash
   git pull --rebase origin main
   ```
   - Rebasing rewrites the commit history to avoid merge commits.

---

### **Pull Request: Collaboration and Review**
A **pull request** (PR) is a way to request a code review and propose merging your changes into another branch (e.g., from `feature/login` to `develop` or `main`). PRs are commonly used in platforms like GitHub, GitLab, and Bitbucket.

#### **Steps to Create and Work with Pull Requests:**
1. **Push your feature branch to the remote repository:**
   ```bash
   git push origin feature/login
   ```

2. **Open a pull request:**
   - Navigate to your repository on GitHub/GitLab.
   - Select the branch you want to merge from (e.g., `feature/login`) and the branch you want to merge into (e.g., `develop` or `main`).
   - Provide a detailed description of the changes and why they are necessary.

3. **Collaborate on the PR:**
   - Team members review the PR, add comments, suggest changes, or approve it.
   - Address any feedback and push additional commits if necessary:
     ```bash
     git add .
     git commit -m "Addressed review feedback"
     git push
     ```

4. **Merge the PR:**
   - Once approved and all checks (e.g., CI tests) pass, merge the PR into the target branch.
   - Delete the feature branch if it’s no longer needed to keep the repository clean.

---

### **Pull vs. Pull Request: Key Differences**
| **Aspect**           | **Pull**                                      | **Pull Request (PR)**                         |
|-----------------------|-----------------------------------------------|-----------------------------------------------|
| **Purpose**           | Synchronize your local branch with remote.   | Propose changes for review and collaboration. |
| **Scope**             | Local branch updates.                        | Repository-wide process for merging code.     |
| **Command/Interface** | CLI: `git pull`                              | GUI/Platform-based (e.g., GitHub PR feature). |
| **Usage**             | For updating your branch.                    | For collaborating and merging feature branches. |

---

### **How They Work Together**
1. **Pull First:** Before creating or merging a PR, pull the latest changes from the target branch to ensure your branch is up-to-date and avoid conflicts.
2. **Push and PR:** Push your branch to the remote repository and open a PR to integrate your work into the main or develop branch.
3. **Finalize by Merging the PR:** Once the PR is reviewed and approved, merge it into the target branch. After merging, pull the latest changes locally to sync your branch.

\

When multiple developers work on the same file and a merge conflict arises in Git, resolving it requires careful handling to ensure that changes from all parties are incorporated correctly. Here's how you can approach resolving the conflict ? 


---

### **1. Identify the Conflict**
- After attempting a merge, Git will alert you about the conflicting files and indicate the conflicts within the file(s).
- Use the command:
  ```bash
  git status
  ```
  to see which files have conflicts.

---

### **2. Open the Conflicted File**
Conflicts are marked within the file with conflict markers:
```plaintext
<<<<<<< HEAD
Changes from your branch
=======
Changes from the branch being merged
>>>>>>> branch-name
```

These markers show:
- **HEAD**: Your branch's changes.
- **Below `=======`**: The incoming branch's changes.

---

### **3. Resolve the Conflict**
There are a few ways to resolve conflicts:
1. **Manually Edit the File:**
   - Open the conflicted file in your text editor or IDE.
   - Review and decide how to merge the conflicting changes.
   - Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`) after resolving.

2. **Use a Merge Tool:**
   - Many IDEs and tools (e.g., Visual Studio Code, IntelliJ IDEA) offer visual merge tools to simplify conflict resolution.
   - From the CLI:
     ```bash
     git mergetool
     ```
     Git will open your configured merge tool for resolving conflicts.

3. **Accept Incoming or Current Changes:**
   - If you want to keep one side entirely:
     ```bash
     git checkout --ours conflicted-file.txt
     git checkout --theirs conflicted-file.txt
     ```
   - Replace `ours` with your branch's version or `theirs` with the incoming branch's version.

---

### **4. Mark the Conflict as Resolved**
After resolving the conflict in all files:
```bash
git add conflicted-file.txt
```

---

### **5. Complete the Merge**
Commit the resolved changes to complete the merge:
```bash
git commit -m "Resolved merge conflict in conflicted-file.txt"
```

If you’re rebasing:
```bash
git rebase --continue
```

---

### **6. Test the Changes**
Ensure the code works as intended after resolving conflicts by running tests or the application.

---

### **Best Practices for Avoiding and Resolving Conflicts**
1. **Communicate with Team Members:**
   - Avoid working on the same sections of code simultaneously.
   - Inform others of major changes.

2. **Pull Frequently:**
   - Regularly pull the latest changes from the shared branch (`main` or `develop`) into your local branch to minimize divergence.

3. **Divide Work Clearly:**
   - Split tasks to minimize overlapping work on the same files.

4. **Use Continuous Integration (CI):**
   - Automated builds and tests help catch issues early.



### Scenario:
You’re working on a feature in the `dev` branch and realize you need to quickly switch to `main` to make a critical change, but you don’t want to commit unfinished work in `dev` just yet.

### Workflow Example:
1. **Start working on a feature in `dev` branch:**
   You're working on a feature in the `dev` branch, and you modify several files, but you're not ready to commit them yet.
   ```bash
   git checkout dev
   # You make changes to some files
   ```

2. **Realize you need to switch to `main` to make urgent fixes:**
   You need to change something important in the `main` branch (e.g., update the port number). You don’t want to commit unfinished work in `dev`, so you use `git stash` to save your changes temporarily.
   ```bash
   git stash
   ```

3. **Switch to `main` branch:**
   Now, you can safely switch to the `main` branch to address the urgent issue without affecting your `dev` branch.
   ```bash
   git checkout main
   ```

4. **Make the necessary changes in `main`:**
   On the `main` branch, make the required changes and commit them.
   ```bash
   # Edit files in the `main` branch
   git add .
   git commit -m "Fix port number in main"
   git push origin main
   ```

5. **Switch back to `dev` and apply the stashed changes:**
   Once you’ve committed your changes in `main`, return to your `dev` branch. To retrieve your saved work from the stash, use `git stash pop`.
   ```bash
   git checkout dev
   git stash pop
   ```

### When to Use `git stash pop`:
- **Use it when you need to temporarily save your local changes** while switching between branches or tasks.
- **If you want to apply the stashed changes and remove them from the stash list**, use `git stash pop`. It will both restore your changes and clean up your stash list.
- Example: After making changes in `main` and coming back to `dev`, you can apply your saved progress from the stash.

### When NOT to Use `git stash pop`:
- **If you want to keep the stash entry for future use**, don’t use `git stash pop`. Instead, use `git stash apply`. This will apply the stashed changes but leave the stash intact for future use.
- **If there’s a conflict** when applying the stash, it’s better to inspect the changes first (by using `git stash show` or `git stash list`) to avoid overwriting important changes unintentionally.

### In Summary:
- **`git stash`**: Temporarily saves your changes without committing them, useful when you need to switch branches or work on something else quickly.
git pop = Apply changes + remove from stash.
git apply = Apply changes + leave in stash 

### Git Cherry-pick and Git Revert: Scenarios and Examples

Both `git cherry-pick` and `git revert` are used to manage commits, but they are employed in different contexts. Here’s when you can use each, along with examples.

---

### **Git Cherry-pick**
**Scenario**: You want to apply a specific commit from one branch to another without merging the entire branch.

**Use case**: Suppose you’ve committed a bug fix in a feature branch (`feature/login`) and now need to apply that fix to the `main` branch. Instead of merging the entire feature branch into `main`, you cherry-pick the specific commit that contains the bug fix.

**Steps**:
1. Identify the commit hash of the change you want to apply. You can get this by using `git log`.
   ```bash
   git log
   ```
   Output might look like:
   ```
   commit 123abc456def789gh
   Author: Your Name <your@email.com>
   Date:   Thu Dec 2 10:20:30 2024 +0000

       Fix bug in login form
   ```
   The commit hash is `123abc456def789gh`.

2. Switch to the branch where you want to apply the change (`main` in this case):
   ```bash
   git checkout main
   ```

3. Apply the cherry-pick:
   ```bash
   git cherry-pick 123abc456def789gh
   ```

4. Resolve any conflicts (if needed), commit the changes, and push.

**Example Output**:
```
$ git cherry-pick 123abc456def789gh
[main 345def678abc] Fix bug in login form
 1 file changed, 2 insertions(+), 1 deletion(-)
```

**Key Points**:
- **Use `cherry-pick`** when you want to selectively apply specific commits from one branch to another without merging the entire branch.
- **Pros**: Great for small, isolated changes like bug fixes or specific features.
- **Cons**: Can lead to duplication of commits if used excessively.

---

### **Git Revert**
**Scenario**: You need to undo the effects of a commit on a branch, but you want to keep the history intact. This is often used when you accidentally push a change that needs to be undone without rewriting the commit history.

**Use case**: Imagine you’ve pushed a commit to the `main` branch that introduces a bug. Instead of modifying history (which could disrupt collaboration), you create a new commit that reverses the changes made by the problematic commit.

**Steps**:
1. Identify the commit hash of the change you want to revert. As with `cherry-pick`, you can find this using `git log`:
   ```bash
   git log
   ```
   Let’s assume the commit hash to revert is `123abc456def789gh`.

2. Revert the commit:
   ```bash
   git revert 123abc456def789gh
   ```

3. Git will automatically generate a new commit that undoes the changes in the commit you specified. If there are conflicts, Git will prompt you to resolve them.

4. After resolving conflicts (if any), commit and push the changes:
   ```bash
   git push origin main
   ```

**Example Output**:
```
$ git revert 123abc456def789gh
[main 987xyz654cba] Revert "Fix bug in login form"
 1 file changed, 2 deletions(-)
```

**Key Points**:
- **Use `revert`** when you want to create a new commit that undoes the effects of a previous commit without modifying the commit history.
- **Pros**: Keeps history intact and avoids rewriting history in shared repositories.
- **Cons**: Adds another commit to the history, which may clutter the logs in some cases.

---

### Summary:

- **`git cherry-pick`**: Use when you need to apply a specific commit from one branch to another. It’s selective and doesn’t merge entire branches.
- **`git revert`**: Use when you need to undo the changes made by a commit while maintaining the commit history. It’s a safer option when working in a shared team environment.

cheetsheet : https://www.atlassian.com/git/tutorials/atlassian-git-cheatsheet
