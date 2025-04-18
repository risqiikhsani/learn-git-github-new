You can cancel the latest Git commit in a couple of ways, depending on what exactly you want:

---

### 🔄 Option 1: **Undo the commit but keep the changes**
> Great if you just want to tweak the commit message or make edits before recommitting.

```bash
git reset --soft HEAD~1
```

✅ This moves your branch back one commit, but **keeps your code changes staged**.

---

### 🔧 Option 2: **Undo the commit and unstage the changes**
> Leaves your changes in your working directory (like you never committed).

```bash
git reset --mixed HEAD~1
```

✅ Changes stay in your files, but are no longer staged.

---

### 💥 Option 3: **Undo the commit and delete the changes**
> Dangerous — this erases both the commit *and* the code.

```bash
git reset --hard HEAD~1
```

⚠️ This will **permanently delete** the latest commit **and all changes**. Only use if you're sure.

---

Let me know your goal and I’ll suggest the safest one!