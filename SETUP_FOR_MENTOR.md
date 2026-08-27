# 🛠️ Maintainer Setup & Operations (dành cho Tommy)

> Repo này là **lộ trình self-study** — team tự làm ở nhà theo `WORKSHOP.md`, review chéo nhau. Anh chỉ setup **một lần** trước khi giao, sau đó vận hành async (review PR, trả lời issue).

**Trạng thái hiện tại:**

- ✅ Repo đã live: **https://github.com/SOY-Digital/github-workshop** (org SOY-Digital)
- ✅ Local repo: `/Users/tommynguyen/Developer/work/SOY-SM-WORK/github-workshop` (remote đã trỏ org)
- ✅ **Bước 1 done (2026-08-27):** collaborators đã invite — `anhsoyagency`, `ngocsoyasw` đã accept · `liemsoy`, `QuangSoyAgency` đã mời nhưng **chưa accept** (nhắc họ check email/spam; khi accept xong thì vào issue #1, #3 self-assign)
- ✅ **Bước 2 done:** squash-only + auto-merge + auto-delete branch đã bật qua API; branch protection `main` (1 approval, dismiss stale, conversation resolution, admin bypass)
- ✅ **Bước 3 done:** 4 issue đã tạo — [#1](https://github.com/SOY-Digital/github-workshop/issues/1) liemsoy · [#2](https://github.com/SOY-Digital/github-workshop/issues/2) ngocsoyasw · [#3](https://github.com/SOY-Digital/github-workshop/issues/3) QuangSoyAgency · [#4](https://github.com/SOY-Digital/github-workshop/issues/4) anhsoyagency — label `good first issue`; #1, #3 chưa assign được (pending invite accept)
- ✅ **Bước 4 done:** PR test #5 verify — squash-only hoạt động, merge bị chặn khi thiếu approval (`BLOCKED`), auto-merge path OK (SQUASH) — PR đã close + branch đã xoá; clone test từ máy bên ngoài pass

---

## Phần A — Setup một lần (trước khi giao repo cho team, ~20 phút)

### Bước 1 — Thêm 4 thành viên vào repo (3 phút)

Repo thuộc org nên có 2 cách:

**Cách A — đơn giản (outside collaborators):**
Repo → **Settings → Collaborators and teams → Add people** → add 4 người:
- `liemsoy`
- `ngocsoyasw`
- `QuangSoyAgency`
- `anhsoyagency`

Role: **Write** (đủ quyền push branch + mở PR + approve PR khác).

**Cách B — qua org Team (nếu muốn quản tập trung sau này):**
Org SOY-Digital → **Teams → New team** (VD `workshop`) → add 4 bạn → vào repo Settings → Collaborators and teams → add team `workshop` với role **Write**.

> ⚠️ Nhắc các bạn **check email (kể cả spam)** và Accept invite — bài đầu tiên của lộ trình sẽ fail ngay tại `git clone`/`git push` nếu chưa accept.

### Bước 2 — Cấu hình merge & branch protection (5 phút)

**2a. Merge settings** — Repo → **Settings → General → Pull Requests**:

| Setting | Value |
|---|---|
| Allow merge commits | ❌ OFF |
| Allow squash merging | ✅ ON ("Commit title + commit message") |
| Allow rebase merging | ❌ OFF |
| **Automatically delete head branches** | ✅ ON |

→ Học viên được hướng dẫn bấm **"Squash and merge"** — settings này đảm bảo đó là nút duy nhất, và branch tự xoá sau merge.

**2b. Branch protection cho `main`** — **Settings → Branches → Add branch protection rule**:

| Setting | Value |
|---|---|
| Branch name pattern | `main` |
| Require a pull request before merging | ✅ ON |
| Require approvals | ✅ ON, minimum **1 approval** |
| Dismiss stale pull request approvals when new commits are pushed | ✅ ON |
| Require conversation resolution before merging | ✅ ON |
| Include administrators | ❌ OFF (anh vẫn fix trực tiếp được khi cần gấp) |
| Allow force pushes / deletions | ❌ OFF |

### Bước 3 — Tạo 4 issue mở đầu (5 phút)

**Issues → New issue → Feature Request** template:

| Title | Assignee |
|---|---|
| `[FEAT] Add intro page for liemsoy` | `liemsoy` |
| `[FEAT] Add intro page for ngocsoyasw` | `ngocsoyasw` |
| `[FEAT] Add intro page for QuangSoyAgency` | `QuangSoyAgency` |
| `[FEAT] Add intro page for anhsoyagency` | `anhsoyagency` |

Label `good first issue` cho cả 4.

### Bước 4 — Verify trước khi giao (5 phút)

- [ ] 4 thành viên đã Accept invite
- [ ] Merge settings + auto-delete đã bật (Bước 2a)
- [ ] `main` đã protected (Bước 2b)
- [ ] 4 issue đã tạo, assignee đúng
- [ ] Tạo 1 PR test → verify template load đúng + chỉ thấy nút "Squash and merge" → close + xoá branch test
- [ ] Test clone từ máy khác được

### Bước 5 — Giao repo cho team

Gửi message đại loại:

> Các bạn làm lộ trình tự học GitHub trong repo `SOY-Digital/github-workshop` — mở `WORKSHOP.md`, làm từ Phần 0, mỗi phần có self-check. Tự làm theo tốc độ riêng,review chéo nhau, gặp issue label `question`. Anh review PR khi rảnh, không cần chờ anh mới làm tiếp.

---

## Phần B — Vận hành async (định kỳ, ~15-30 phút/tuần)

| Việc | Tần suất | Cách |
|---|---|---|
| Review PR còn treo | 1-2 lần/tuần | Tab Pull requests → filter "Awaiting your review". Học viên được quyền tự merge khi có approval chéo — anh chỉ cần approve hoặc comment, không cần bấm merge hộ |
| Trả lời issue `question` | Trong ngày làm việc | Tab Issues → sort by newest. Khuyến khiché học viên trả lời nhau trước khi anh vào |
| Check tiến độ team | Tuần 1 lần | Insights → Contributors + đếm PR merged của từng bạn; bạn nào 0 hoạt động > 1 tuần → nhắn riêng |
| Xoá branch drill dư | Tháng 1 lần | Tab Branches → xoá branch `docs/my-rule` cũ (học viên có thể quên xoá local push) |
| Ghi nhận hoàn thành | Khi có issue `[FEAT] Hoàn thành lộ trình` | React 👍 + comment chúc mừng; tập hợp để tính cho buổi review nâng cao |

---

## 📞 Troubleshooting nhanh

| Vấn đề | Giải pháp |
|---|---|
| Học viên không thấy repo | Chưa accept invite → check email (kể cả spam) |
| `git push` báo auth fail | Học viên chưa setup PAT/SSH → trỏ họ tới WORKSHOP.md → "Xử lý lỗi thường gặp" |
| Commit không có avatar | `user.email` không khớp email GitHub → WORKSHOP.md Phần 0 đã giải thích |
| `main` bị lock với anh | "Include administrators" đang OFF nên anh vẫn push trực tiếp được; nếu tắt nhầm → Settings → Branches sửa lại |
| Conflict drill không nổ conflict | Học viên sửa 2 dòng khác nhau thay vì cùng dòng 3 — exercises/03 yêu cầu rõ "cùng sửa dòng 3" |
| Học viên commit sai author | `git commit --amend --author="Tên <email-đúng>"` rồi `git push --force-with-lease` |
| Học viên merge nhầm thứ gì đó vào main | revert qua PR: `git revert <sha>` — cũng là dịp dạy thêm 1 khái niệm |

---

**Setup một lần:** ~20 phút · **Vận hành:** ~15-30 phút/tuần
