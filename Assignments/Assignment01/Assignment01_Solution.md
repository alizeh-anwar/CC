# Assignment 01
## Git, Gitea, GitHub, Git LFS, and GitHub Pages

**Fatima Jinnah Women University** | Cloud Computing (BSE-410)

### Student Information

| Field | Details |
|---|---|
| Student Name | Alizeh Anwar |
| Registration No. | FA24B1-SE-038 |
| Section | B |
| Program / Semester | BS (Software Engineering) - V |
| Course | Cloud Computing (BSE-410) |
| Assignment | Assignment 01: Git, Gitea, GitHub, Git LFS, and GitHub Pages |
| GitHub Username | alizeh-anwar |
| Submission Date | October 10, 2026 |

---

## Task 1: Install Gitea and Push a Repository from the Ubuntu Server

### Step 1.1: Install and Run Gitea

**Commands used**

```bash
sudo apt update -y && sudo apt install -y docker.io curl
cd ~/Gitea && docker compose up -d
docker compose ps
curl -sS -o /dev/null -w "Gitea HTTP status: %{http_code}\n" http://127.0.0.1:3000/
```

**Screenshot:** Figure 1: `task1_gitea_running.png`

### Step 1.2: Create and Push the Initial Repository

**Commands used**

```bash
cd ~/Assignment01 && git init && git branch -M main
git add README.md && git commit -m "Add student information"
git remote add gitea http://<gitea-username>@127.0.0.1:3000/<gitea-username>/Assignment01.git
git remote -v
git push -u gitea main
```

**Screenshot:** Figure 2: `task1_gitea_push.png`

### Step 1.3: Verify the Gitea Repository

**Screenshot:** Figure 3: `task1_gitea_repository.png`

---

## Task 2: Push the Same Repository to GitHub

### Step 2.1: Add GitHub Remote and Verify Both Remotes

**Commands used**

```bash
cd ~/Assignment01
git remote add github https://github.com/<your-github-username>/Assignment01.git
git remote -v
```

**Screenshot:** Figure 4: `task2_remotes.png`

### Step 2.2: Push to GitHub

**Command used**

```bash
git push -u github main
```

**Screenshot:** Figure 5: `task2_github_push.png`

### Step 2.3: Verify the GitHub Repository

**Screenshot:** Figure 6: `task2_github_repository.png`

---

## Task 3: Track Three Large Files with Git LFS

### Step 3.1: Configure Git LFS

**Commands used**

```bash
cd ~/Assignment01
git lfs install
git lfs version
git lfs track "*.bin"
cat .gitattributes
```

**Screenshot:** Figure 7: `task3_lfs_setup.png`

### Step 3.2: Create and Verify Three LFS Files

**Commands used**

```bash
truncate -s 101M large-file-1.bin
truncate -s 102M large-file-2.bin
truncate -s 103M large-file-3.bin
git add .gitattributes large-file-1.bin large-file-2.bin large-file-3.bin
git lfs ls-files --size
```

**Screenshot:** Figure 8: `task3_lfs_files.png`

### Step 3.3: Commit and Push the LFS Files

**Commands used**

```bash
git commit -m "Add three files using Git LFS"
git push github main
```

**Screenshot:** Figure 9: `task3_lfs_push.png`

---

## Task 4: Create a Portfolio or CV with GitHub Pages

### Step 4.1: Create and Push the Portfolio Repository

- Repository name: `<your-github-username>.github.io`
- Required files: `index.html`, `styles.css`
- Required sections: About Me, Education, Skills, Projects

**Screenshot:** Figure 10: `task4_pages_repository.png`

### Step 4.2: Publish with GitHub Pages

Settings > Pages > Deploy from a branch > main > / (root) > Save

**Screenshot:** Figure 11: `task4_pages_deployment.png`

### Step 4.3: Verify the Live Portfolio

**Screenshot:** Figure 12: `task4_portfolio_live.png`

---

## Assignment Summary

- Installed and ran Gitea on the Ubuntu server using Docker Compose.
- Created a local Git repository on the server and pushed it to Gitea and GitHub using two remotes.
- Authenticated with personal access tokens entered at the password prompt, never inside a URL.
- Configured Git LFS and pushed three files larger than 100 MiB.
- Published a portfolio with GitHub Pages.
