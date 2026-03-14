# Push this folder to your support repo

Replace `REPO_URL` below with your actual support repo URL (e.g. `https://github.com/jonashusby/quizbok-support.git`).

## Option A: Clone the support repo and copy files

```powershell
# From your quizbok folder, clone your empty support repo (use your actual repo URL)
cd c:\Users\jonas\dev\quizbok
git clone REPO_URL support-repo
cd support-repo

# Copy the 3 HTML files from quizbok/support-site into the repo root
copy ..\support-site\index.html .
copy ..\support-site\privacy.html .
copy ..\support-site\terms.html .

# Commit and push
git add index.html privacy.html terms.html
git commit -m "Add Quizboka support site"
git push -u origin main
```

If your default branch is `master` instead of `main`, use `git push -u origin master`.

## Option B: Push from quizbok repo using subtree

Run this from your **quizbok** repo root (after committing the `support-site` folder):

```powershell
cd c:\Users\jonas\dev\quizbok

# Add your support repo as a remote (use your actual repo URL)
git remote add support REPO_URL

# Push only the support-site folder to the support repo's main branch
git subtree push --prefix support-site support main
```

---

## After pushing

1. On GitHub: repo **Settings** → **Pages**.
2. **Source:** Deploy from a branch.
3. **Branch:** `main` (or `master`), **Folder:** `/ (root)`.
4. Save. Your site will be at: `https://<username>.github.io/<repo-name>/`

Use that URL as **Support URL** and `.../privacy.html` as **Privacy Policy URL** in App Store Connect.
