lets say the repo deny direct push to main branch,
but you have modified some files in local, but forgot to create new branch.

If you've made changes directly on the `main` branch (or another branch), but forgot to create a new branch first, no worries — you can still fix it without losing your work. Here's how to do it:

### Scenario: You've modified data on the wrong branch (`main`) and want to move those changes to a new branch.

---

### 1. **Stash your changes (if you haven't committed yet)**
If you’ve made modifications but haven’t committed them yet, you can stash your changes to apply them later:

```bash
git stash
```

This will temporarily save your uncommitted changes. You can then create a new branch and apply those changes.

---

### 2. **Create a new branch**
Create a new branch from the current state (which includes your changes):

```bash
git checkout -b new-branch-name
```

If you've stashed your changes, you can now **apply the stashed changes**:

```bash
git stash pop
```

---

### 3. **Commit your changes**
Now that you're on the correct branch, commit the changes:

```bash
git add .
git commit -m "Your commit message"
```

---

### 4. **Push the new branch to the remote**
Push your new branch to GitHub:

```bash
git push origin new-branch-name
```

---

### 5. **Optional: Revert the changes from the `main` branch**
If you've accidentally committed to `main` but want to revert that commit (because you didn’t intend to change `main` directly), you can use `git reset` or `git revert`.

#### **Option 1: If you want to remove the last commit entirely from `main`**

```bash
git checkout main
git reset --hard HEAD~1
```

This removes the last commit from `main` **completely** (be careful — this will **discard** your changes if they are not in a new branch yet).

#### **Option 2: If you want to keep the changes in your working directory but remove the commit**

```bash
git checkout main
git reset --soft HEAD~1
```

This removes the last commit but **keeps the changes staged** for a new commit.

---

### 6. **Push changes to `main` (if applicable)**
After performing the `reset`, if you want to update `main` on the remote repo, you'll need to force-push:

```bash
git push origin main --force
```

### **Summary of Commands (without stashing)**:
1. Create a new branch: 
   ```bash
   git checkout -b new-branch-name
   ```
2. Stage and commit the changes:
   ```bash
   git add .
   git commit -m "Your commit message"
   ```
3. Push the new branch to GitHub:
   ```bash
   git push origin new-branch-name
   ```
4. (Optional) Revert changes on `main`:
   - If the commit is unwanted, reset it:
     ```bash
     git checkout main
     git reset --hard HEAD~1
     ```

---

This should help you recover from forgetting to create a new branch! Let me know if you have any further questions.