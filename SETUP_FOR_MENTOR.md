# 🛠️ Setup Checklist (dành cho mentor — Tommy)

> File này dành cho anh Tommy. Hoàn thành từng bước trước khi bắt đầu workshop.

**Trạng thái hiện tại:**

- ✅ Repo đã live: **https://github.com/SOY-Digital/github-workshop** (org SOY-Digital)
- ✅ Local repo: `/Users/tommynguyen/Developer/work/SOY-SM-WORK/github-workshop` (remote đã trỏ org)
- ⬜ Các bước 1→4 bên dưới

---

## Bước 1 — Thêm 4 thành viên vào repo (3 phút)

Repo thuộc org nên có 2 cách:

**Cách A — đơn giản (outside collaborators):**
Repo → **Settings → Collaborators and teams → Add people** → add 4 người:
- `liemsoy`
- `ngocsoyasw`
- `QuangSoyAgency`
- `anhsoyagency`

Role: **Write** (đủ quyền push branch + mở PR).

**Cách B — qua org Team (nếu muốn quản tập trung sau này):**
Org SOY-Digital → **Teams → New team** (VD `workshop`) → add 4 bạn → vào repo Settings → Collaborators and teams → add team `workshop` với role **Write**.

> ⚠️ Các bạn phải **check email (kể cả spam)** và Accept invite trước buổi học — tránh tốn 15 phút debug permission denied giữa buổi.

---

## Bước 2 — Cấu hình merge & branch protection (5 phút)

### 2a. Merge settings

Repo → **Settings → General → Pull Requests** section:

| Setting | Value |
|---|---|
| Allow merge commits | ❌ OFF |
| Allow squash merging | ✅ ON (chọn "Commit title + commit message" để tự gom từ commit messages) |
| Allow rebase merging | ❌ OFF |
| **Automatically delete head branches** | ✅ ON |

→ WORKSHOP.md Phần 5.3 hướng dẫn học viên bấm **"Squash and merge"** — settings này đảm bảo nút đó là lựa chọn duy nhất, và branch tự xoá sau merge.

### 2b. Branch protection cho `main`

**Settings → Branches → Add branch protection rule**:

| Setting | Value |
|---|---|
| Branch name pattern | `main` |
| Require a pull request before merging | ✅ ON |
| Require approvals | ✅ ON, minimum **1 approval** |
| Dismiss stale pull request approvals when new commits are pushed | ✅ ON |
| Require conversation resolution before merging | ✅ ON |
| Include administrators | ❌ OFF (anh vẫn fix trực tiếp được khi cần gấp) |
| Allow force pushes / deletions | ❌ OFF |

---

## Bước 3 — Tạo 4 issue mẫu (5 phút)

**Issues → New issue → Feature Request** template:

| Title | Assignee |
|---|---|
| `[FEAT] Add intro page for liemsoy` | `liemsoy` |
| `[FEAT] Add intro page for ngocsoyasw` | `ngocsoyasw` |
| `[FEAT] Add intro page for QuangSoyAgency` | `QuangSoyAgency` |
| `[FEAT] Add intro page for anhsoyagency` | `anhsoyagency` |

Apply label `good first issue` cho cả 4.

---

## Bước 4 — Verify trước buổi học (5 phút)

- [ ] 4 thành viên đã Accept invite (check danh sách trong Settings → Collaborators)
- [ ] Merge settings + auto-delete đã bật (Bước 2a)
- [ ] `main` đã protected (Bước 2b)
- [ ] 4 issue đã tạo, assignee đúng, label `good first issue`
- [ ] Tạo 1 PR test từ branch bất kỳ → verify: PR template load đúng, chỉ thấy nút "Squash and merge" → close PR test, xoá branch test
- [ ] Test clone: `git clone https://github.com/SOY-Digital/github-workshop.git` chạy được trên máy khác

---

## Bước 5 — Trong buổi workshop

Mở `WORKSHOP.md` và follow 7 phần theo thời lượng.

**Mentor notes theo từng phần:**

| Phần | Lưu ý cho anh |
|---|---|
| Phần 3 (branch & commit) | Dành 2 phút check `git config user.email` của từng bạn — email sai là commit mất avatar, lỗi kinh điển của người mới |
| Phần 5 (review & merge) | Ghép chéo review: A review B, B review C... tránh người mở PR tự merge (branch protection sẽ chặn) |
| Phần 6 (conflict drill) | **Quan trọng:** merge PR người A trước, sau đó cả team nhìn màn hình người B thấy conflict xuất hiện — file drill `exercises/conflict-target.md` thiết kế cả 2 cùng sửa dòng 3 nên chắc chắn conflict |
| Phần 7 (issues) | Nhắc học viên dùng `Closes #X` trong PR bài tập 2 |

---

## 📞 Troubleshooting nhanh cho mentor

| Vấn đề | Giải pháp |
|---|---|
| Học viên không thấy repo | Chưa accept invite → check email (kể cả spam) |
| `git push` báo auth fail | Hướng dẫn dùng Personal Access Token (WORKSHOP.md → Xử lý lỗi thường gặp) |
| Commit không có avatar | `user.email` không khớp email GitHub → xem WORKSHOP.md phần chuẩn bị |
| `main` bị lock, anh push không được | Đó là branch protection — nếu thật cần gấp: PR như thường, hoặc tắt rule "Include administrators" đã để OFF thì admin vẫn push được trực tiếp |
| Conflict drill không nổ conflict | Kiểm tra cả 2 có thực sự sửa cùng dòng 3 trong `exercises/conflict-target.md` (không phải dòng khác) |
| Học viên commit sai author | `git commit --amend --author="Tên <email-đúng>"` rồi `git push --force-with-lease` |

---

**Estimated total setup time:** ~20 phút
**Workshop duration:** ~2.5 giờ
