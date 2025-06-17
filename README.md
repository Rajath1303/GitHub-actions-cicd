# 🚀 GitHub Actions CI/CD with Semantic Release

This project automates the release process using **Semantic Release** and **GitHub Actions**.

- ✅ Automatic version bumping in `package.json`
- 📝 Automatic changelog generation (`CHANGELOG.md`)
- 📦 GitHub Releases based on commit messages

---

## 📦 What This Setup Does

- Listens for pull request **merges into `uat`**
- Analyzes commits using Conventional Commits
- Increments the version according to commit type
- Updates `CHANGELOG.md`
- Pushes a new tag and creates a GitHub Release

---

## ✍️ How to Reproduce This Workflow

### ✅ 1. Clone the Repository and Checkout `uat`

```bash
git clone https://github.com/<your-username>/<your-repo>.git
cd <your-repo>
git checkout uat
```

### ✍️ 2. Create a Feature Branch

```bash
git checkout -b feat/test-release
```

### 💡 3. Make a Commit Using Conventional Commits

For example:

```bash
git commit --allow-empty -m "feat!: add new authentication API

BREAKING CHANGE: Old login endpoint removed"
```

Use `feat`, `fix`, or `feat!` with `BREAKING CHANGE:` for proper version bumps.

### 🚀 4. Push the Branch and Open a Pull Request

```bash
git push origin feat/test-release
```

Then open a PR to merge it into `uat`.

### 🔁 5. Merge the Pull Request

Once you merge the PR into `uat`, GitHub Actions will trigger:

- `package.json` version will bump
- `CHANGELOG.md` will update
- A GitHub release will be created with version and commit log

Check the **Actions** tab and **Releases** tab on GitHub to verify.

---

## 📂 Important Files

| File                          | Purpose                                           |
|------------------------------|---------------------------------------------------|
| `.github/workflows/release.yaml` | GitHub Actions workflow for semantic release  |
| `.releaserc`                  | Configuration for semantic-release plugins       |
| `CHANGELOG.md`           | Automatically updated changelog for UAT branch   |

---

## 💬 Commit Message Guidelines

Semantic Release uses Conventional Commits:

| Prefix     | Purpose        | Version Bump |
|------------|----------------|--------------|
| `fix:`     | Bug fix        | Patch        |
| `feat:`    | New feature    | Minor        |
| `feat!:` or `BREAKING CHANGE:` | Breaking change | Major    |

---

## ⚙️ Notes

- CI/CD only runs on PR merges to `uat`.
- The default GitHub token (`secrets.GITHUB_TOKEN`) is used for authentication.
