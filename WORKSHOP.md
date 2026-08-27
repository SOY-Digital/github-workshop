# 📚 SELF-STUDY — Làm quen GitHub Workflow

> Lộ trình **tự học ở nhà** — mỗi bạn tự làm theo tài liệu này theo tốc độ riêng. Không cần chờ ai, không cần hẹn giờ. Tommy review PR khi có thời gian (thường trong ngày làm việc).
>
> **Cách dùng:** làm tuần tự từ trên xuống. Mỗi phần có mục "✅ Xong khi" — chỉ sang phần sau khi self-check pass. Bị kẹt bất kỳ lúc nào → mở issue label `question` (xem Phần 7) hoặc nhắn Tommy.

**Thời lượng tham khảo:** ~2.5-3 giờ liền mạch, hoặc chia nhiều buổi nhỏ — mỗi phần dừng được, không mất tiến độ.

---

## 📋 Phần 0 — Chuẩn bị (15 phút)

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

**Verify quyền truy cập:** Đảm bảo bạn đã nhận invite vào org **SOY-Digital** từ Tommy (check email, kể cả spam) và đã Accept. Chưa nhận → nhắn Tommy gửi lại.

**✅ Xong khi:** `git --version` chạy được, `user.email` khớp email GitHub, đã Accept invite org.

---

## Phần 1 — Làm quen GitHub UI (10 phút)

Tự khám phá repo **https://github.com/SOY-Digital/github-workshop** trên trình duyệt:

| Vùng trên GitHub | Dùng để làm gì |
|---|---|
| **Code** tab | Xem file, browse source |
| **Issues** tab | Đặt câu hỏi, báo bug, đề xuất tính năng |
| **Pull requests** tab | Review code trước khi merge |
| **Actions** tab | CI/CD (sẽ dùng ở mức nâng cao) |
| **Settings** tab | Phân quyền, branch protection (chỉ owner thấy) |
| **Insights → Contributors** | Xem ai đóng góp bao nhiêu |

**Gợi ý tự học:** Mở 1 PR thật của dự án nổi tiếng (ví dụ `facebook/react`) → xem tab "Files changed" → "Commits" → "Reviews" — quan sát người ta mô tả PR và review nhau kiểu gì.

**✅ Xong khi:** Phân biệt được Issues với Pull Requests, biết tab nào để xem diff của PR.

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

<details>
<summary>Đáp án (click mở)</summary>

1. `main` (đây là branch protected)
2. Đếm trong tab Code trên GitHub hoặc `find . -name "*.md" -not -path "./.git/*" | wc -l`
3. `git log --oneline -1` — hiện SHA ngắn + commit message

</details>

**✅ Xong khi:** Trả lời được 3 câu trên mà không cần đoán.

---

## Phần 3 — Tạo branch & commit đầu tiên (20 phút)

> Đây là nội dung của **[Bài tập 1](./exercises/01-personal-intro.md)** — làm theo file đó, quay lại đây khi xong.

Mục tiêu: tạo file `team-pages/<github-user>.md` trên branch riêng và push lên GitHub.

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

**✅ Xong khi:** Branch của bạn xuất hiện trên GitHub (tab Code → dropdown branch), commit có avatar GitHub của bạn.

---

## Phần 4 — Mở Pull Request (15 phút)

Sau khi push thành công, vào repo trên GitHub — sẽ hiện banner vàng với nút **"Compare & pull request"**.

1. Click nút đó
2. **Title:** `feat: add intro page for liemsoy` (copy từ commit message)
3. **Description:** GitHub tự động load template — fill các mục:
   - **Summary:** 1-2 dòng mô tả thay đổi
   - **Changes:** list file đã sửa
   - **How to test:** `git checkout feat/liemsoy-intro && cat team-pages/liemsoy.md`
4. Bên phải:
   - **Reviewers:** add **một bạn khác trong team** (đừng chọn mình, đừng chọn Tommy làm reviewer đầu tiên)
   - **Labels:** `documentation`
5. Click **Create pull request**

**✅ Xong khi:** PR mở thành công, hiện "Awaiting review from ..." và template đã fill.

---

## Phần 5 — Review PR cho bạn khác (15 phút)

> Luật self-study: **mở 1 PR thì phải review 1 PR của bạn khác** — đây là vòng tuần hoàn của teamwork. Có 4 bạn → mỗi PR sẽ luôn có người review mà không cần chờ Tommy.

Trong PR mà bạn được add reviewer (tab **"Files changed"**):

1. Đọc từng dòng thay đổi
2. Hover vào dòng bất kỳ → click **"+"** để comment
3. Chốt bằng 1 trong 3 kiểu review (nút **"Review changes"** góc phải):
   - **Comment:** góp ý, không chặn merge
   - **Approve:** OK, cho merge
   - **Request changes:** phải sửa trước khi merge

**Gợi ý comment hữu ích cho người mới:** "Section X hay, nhưng tên file nên là...", "Đây có phải ý bạn là...?", "Link này bị 404 nè". Tránh chỉ gõ "ok" / "+1" — không có thông tin.

### Khi chính PR của bạn được review

- Có comment → trả lời trong thread; nếu cần sửa → push commit mới lên **cùng branch** (PR tự cập nhật)
- Có "Request changes" → sửa xong push, rồi click **"Re-request review"** để người review check lại
- Có ≥ 1 approval → tự bấm **"Squash and merge"** (repo cấu hình squash + auto-delete branch) — không cần chờ ai cho phép

```bash
# Sau khi merge, dọn local:
git checkout main
git pull origin main
git branch -d feat/liemsoy-intro
```

**✅ Xong khi:** Bạn đã approve hoặc comment ít nhất 1 PR của bạn khác, và PR của bạn đã được merge (bởi bạn sau khi có approval).

---

## Phần 6 — Xử lý Merge Conflict (20 phút — bài khó nhất)

> Đây là nội dung của **[Bài tập 3](./exercises/03-merge-conflict-drill.md)** — drill solo 100% local, tự tạo conflict thật rồi tự resolve. Làm theo file đó.

Nội dung chính bạn sẽ học:
- Cách tạo tình huống 2 branch cùng sửa 1 dòng
- Đọc 3 markers `<<<<<<<`, `=======`, `>>>>>>>`
- Quyết định giữ gì và gộp 2 phía

**✅ Xong khi:** Hoàn thành checklist trong Bài tập 3.

---

## Phần 7 — Issues: cách hỏi khi bị kẹt (10 phút)

Tự học không có nghĩa học một mình — **issue là kênh hỏi chính** của repo này:

1. Tab **Issues → New issue** → chọn template **Question**
2. Mô tả: bạn đang làm bước nào, chạy lệnh gì, thấy lỗi gì (paste đầy đủ error message)
3. Điền tiêu đề rõ: `[QUESTION] git push báo Permission denied dù đã accept invite`

Mẹo hỏi hiệu quả (áp dụng luôn cho Slack):
- Paste **full error message**, đừng chụp màn hình cropped
- Nêu command đã chạy + kết quả mong đợi vs kết quả thực tế
- Nêu những gì đã thử

**Bonus tự học:** Mỗi bạn sau khi xong lộ trình, mở 1 issue Feature Request đề xuất cải thiện repo (thêm bài tập, đổi format...) — đây cũng là cách luyện viết issue.

**Reference issue trong PR:** thêm `Closes #5` vào PR description → issue tự đóng khi PR merge.

**✅ Xong khi:** Đã mở ít nhất 1 issue (question hoặc feature request).

---

## 🎓 Checklist tốt nghiệp

Tự đánh giá — tick đủ là xong lộ trình:

- [ ] `git config user.email` khớp email GitHub (commit có avatar)
- [ ] Clone repo thành công
- [ ] Tạo branch riêng, commit, push lên GitHub
- [ ] Mở PR đúng template + add reviewer
- [ ] Review (comment/approve) PR của ít nhất 1 bạn khác
- [ ] Merge PR sau khi có approval, sync main về local
- [ ] Tự tạo conflict, resolve, hiểu 3 markers
- [ ] Mở ít nhất 1 issue và biết dùng `Closes #X`

**Xong hết?** Chúc mừng 🎉 — mở 1 issue `[FEAT] Hoàn thành lộ trình self-study` với tên bạn để ghi nhận (và để Tommy biết ai cần bài nâng cao: gh CLI, GitHub Actions, CI/CD...).

---

## Xử lý lỗi thường gặp

### `git push` báo `Permission denied`

→ Bạn chưa Accept invite org, hoặc chưa setup auth cho git.

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

→ Có người merge lên main trước bạn:

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
git commit --amend --author="Liem Bui <liem@asw.global>"
```

### Vim mở ra và không thoát được (sau lệnh `git commit`)

Gõ `:wq` rồi Enter (ghi & thoát). Muốn dùng editor khác: `git config --global core.editor "code --wait"`.

---

## 📚 Tài liệu tham khảo

- [GitHub Docs — Pull Requests](https://docs.github.com/en/pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Pro Git book (free)](https://git-scm.com/book/en/v2)
- [Oh My Git! — game học git interactive](https://ohmygit.org/)
- [Learn Git Branching — visualizer cực tốt](https://learngitbranching.js.org/)

---

**Maintainer:** Tommy (`thien-soy`) — review PR trong giờ làm việc, hỏi gấp thì Slack
**Last updated:** phiên bản self-study
