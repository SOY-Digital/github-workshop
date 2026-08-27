# 🚀 WORKSHOP — Làm quen GitHub Workflow

> File này là **script chi tiết** cho buổi workshop. Mỗi phần có thời lượng ước tính. Mentor đọc trước, học viên follow theo.

**Thời lượng tổng:** ~2.5 giờ (có thể chia 2 buổi nếu cần)

---

## 📋 Chuẩn bị trước buổi học (15 phút — làm TRƯỚC khi bắt đầu)

Mỗi học viên cần:

```bash
# 1. Cài git (nếu chưa có)
# macOS: xcode-select --install  |  Windows: tải git-scm.com  |  Linux: apt install git

# 2. Cấu hình git user (BẮT BUỘC)
git config --global user.name "Liem Bui"       # ← tên hiển thị của bạn (tên thật, tự do)
git config --global user.email "liem@asw.global" # ← email PHẢI trùng email tài khoản GitHub của bạn

# 3. Verify
git config --global user.name
git config --global user.email
git --version
```

**⚠️ Quan trọng — cách GitHub nhận biết commit là của AI:**
- GitHub map commit với tài khoản của bạn qua **`user.email`**, KHÔNG phải `user.name`.
- Nếu email sai → commit vẫn push được nhưng **không có avatar, không được tính vào contributions** của bạn.
- Xem email tài khoản GitHub của bạn tại: `github.com` → Settings → **Emails** (đăng nhập bằng account của bạn).
- Nếu không muốn lộ email thật: bật "Keep my email addresses private" rồi dùng email dạng `12345678+liemsoy@users.noreply.github.com` (GitHub hiện sẵn email này trong trang Emails).

**Verify quyền truy cập:** Đảm bảo bạn đã nhận invite vào org **SOY-Digital** từ Tommy (check email, kể cả spam) và đã Accept.

---

## Phần 1 — Tour GitHub UI (10 phút)

Mentor chia sẻ màn hình, walk-through:

| Vùng trên GitHub          | Dùng để làm gì                                  |
|---------------------------|-------------------------------------------------|
| **Code** tab              | Xem file, browse source                         |
| **Issues** tab            | Đặt câu hỏi, báo bug, đề xuất tính năng        |
| **Pull requests** tab     | Review code trước khi merge                     |
| **Actions** tab           | CI/CD (sẽ dùng ở workshop nâng cao)            |
| **Settings** tab          | Phân quyền, branch protection (chỉ owner)       |
| **Insights → Contributors** | Xem ai đóng góp bao nhiêu                     |

**Demo nhanh:** Mở 1 PR bất kỳ trên GitHub của ai đó (ví dụ React, Vue) → xem tab "Files changed" → "Commits" → "Reviews".

---

## Phần 2 — Clone & khám phá repo (10 phút)

```bash
# Clone về máy
git clone https://github.com/SOY-Digital/github-workshop.git
cd github-workshop

# Xem trạng thái
git status
git branch -a
git log --oneline -10

# Mở README.md bằng editor yêu thích (VSCode, Sublime, vim...)
code .           # VSCode
# hoặc
open README.md   # macOS — Windows dùng: start README.md
```

**Bài tập nhỏ (5 phút):** Trả lời trong đầu:
1. Branch mặc định là gì?
2. Có bao nhiêu file `.md` trong repo?
3. Commit gần nhất là gì?

---

## Phần 3 — Tạo branch & commit đầu tiên (20 phút)

Mục tiêu: Mỗi người tạo file `team-pages/<github-user>.md` và push lên branch riêng.

```bash
# 1. Đảm bảo đang ở main và sync mới nhất
git checkout main
git pull origin main

# 2. Tạo branch riêng (đặt tên theo GitHub user)
git checkout -b feat/liemsoy-intro

# 3. Copy file mẫu và sửa
cp team-pages/_template.md team-pages/liemsoy.md        # macOS/Linux
# Windows PowerShell: Copy-Item team-pages/_template.md team-pages/liemsoy.md

# Mở file vừa tạo bằng editor, điền:
# - Tên, role, GitHub user
# - 1 dòng giới thiệu bản thân
# - 1 thứ bạn muốn học ở workshop

# 4. Xem thay đổi
git diff

# 5. Stage & commit
git add team-pages/liemsoy.md
git commit -m "feat: add intro page for liemsoy"

# 6. Push branch lên GitHub
git push -u origin feat/liemsoy-intro
```

**⚠️ Nếu gặp lỗi authentication:** xem mục [Xử lý lỗi thường gặp](#xử-lý-lỗi-thường-gặp) ở cuối file.

---

## Phần 4 — Mở Pull Request (15 phút)

Sau khi push thành công, GitHub sẽ hiện banner vàng với nút **"Compare & pull request"**.

1. Click nút đó
2. **Title:** `feat: add intro page for liemsoy` (copy từ commit message)
3. **Description:** GitHub tự động load template — fill các mục:
   - **Summary:** 1-2 dòng mô tả thay đổi
   - **Changes:** list file đã sửa
   - **How to test:** `git checkout feat/liemsoy-intro && cat team-pages/liemsoy.md`
4. Bên phải:
   - **Reviewers:** add 1 người khác trong team (đừng chọn mình)
   - **Labels:** `documentation`
   - **Projects / Milestone:** bỏ qua
5. Click **Create pull request**

**Mentor walk-through:** Cách đọc tab "Files changed", để lại comment inline, suggest edit.

---

## Phần 5 — Review PR (20 phút)

### 5.1 — Reviewer đọc code

Trong PR trên GitHub:

1. Tab **"Files changed"** → đọc từng dòng
2. Hover vào dòng bất kỳ → click **"+"** để comment
3. Có 3 kiểu review:
   - **Comment:** góp ý, không block merge
   - **Approve:** OK, có thể merge
   - **Request changes:** phải sửa trước khi merge

### 5.2 — Author phản hồi

Khi có comment → author:
- Trả lời trực tiếp trong thread comment
- Nếu có thay đổi → push commit mới lên cùng branch
- Click **"Re-request review"** để reviewer check lại

### 5.3 — Merge

Khi PR có ≥ 1 approval:
- Click **"Squash and merge"** (repo này cấu hình squash làm mặc định — gom mọi commit trên branch thành 1 commit gọn trong `main`)
- **Quan trọng:** Repo đã bật tự động xóa branch sau merge. Nếu vẫn thấy branch, click nút **"Delete branch"**. Local thì tự dọn:

```bash
git checkout main
git pull origin main
git branch -d feat/liemsoy-intro
```

---

## Phần 6 — Xử lý Merge Conflict (20 phút — BONUS)

Mentor tạo sẵn conflict scenario: 2 người cùng sửa `README.md`. Học viên tự resolve.

```bash
# Trong khi đang ở branch của mình, sync main mới nhất
git fetch origin
git merge origin/main
# hoặc
git rebase origin/main

# Nếu có conflict:
# <<<<<<< HEAD
#   code của bạn
# =======
#   code từ main
# >>>>>>> origin/main

# Sửa file thủ công, xóa markers, rồi:
git add .
git commit -m "fix: resolve merge conflict in README.md"
git push
```

---

## Phần 7 — Issues & Discussions (15 phút)

### 7.1 — Tạo issue

```bash
# Cách 1: Trên GitHub UI → tab Issues → New issue
# Cách 2: Dùng template trong .github/ISSUE_TEMPLATE/
```

Mỗi học viên tạo **1 issue** đề xuất cải thiện workshop (ví dụ: thêm bài tập, đổi format, thêm template...).

### 7.2 — Reference issue trong PR

Trong PR description, thêm `Closes #5` → khi merge PR, issue tự động đóng.

---

## 🎓 Kết thúc & tự đánh giá

Checklist mỗi người tự check:

- [ ] Đã cấu hình `git config --global user.name` đúng GitHub handle
- [ ] Đã clone repo thành công
- [ ] Đã tạo branch riêng và push lên
- [ ] Đã mở ít nhất 1 PR
- [ ] Đã review ít nhất 1 PR của người khác
- [ ] Đã merge PR và sync main về local
- [ ] (Bonus) Đã xử lý 1 merge conflict
- [ ] (Bonus) Đã tạo 1 issue và link vào PR

---

## Xử lý lỗi thường gặp

### `git push` báo `Permission denied`

→ Bạn chưa được Tommy add làm Collaborator, hoặc chưa setup SSH/token.

```bash
# Nhanh nhất: dùng HTTPS với Personal Access Token
# 1. Tạo token: GitHub → Settings → Developer settings → Personal access tokens → Tokens (classic) → Generate new token
# 2. Chọn scope: repo
# 3. Khi push lần đầu, nhập username + token (không phải password)
```

Hoặc setup SSH:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
# Copy toàn bộ output → GitHub → Settings → SSH and GPG keys → New SSH key
ssh -T git@github.com  # test
```

### `git commit` không có gì để commit

→ Bạn chưa `git add` file. Chạy `git add .` trước.

### `git push` báo `non-fast-forward`

→ Có người push lên main trước bạn:

```bash
git pull --rebase origin main
git push
```

### Quên mất branch

```bash
git branch -a          # list tất cả branch
git checkout main
git pull
```

### Commit nhầm author

```bash
git commit --amend --author="liemsoy <liem@example.com>"
```

---

## 📚 Tài liệu tham khảo

- [GitHub Docs — Pull Requests](https://docs.github.com/en/pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Pro Git book (free)](https://git-scm.com/book/en/v2)
- [Oh My Git! — game học git interactive](https://ohmygit.org/)

---

**Mentor:** Tommy (`thien-soy`)
**Last updated:** Workshop Day 1
