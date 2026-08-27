# 🛠️ Setup Checklist (dành cho mentor — Tommy)

> File này dành cho anh Tommy. Hoàn thành từng bước trước khi bắt đầu workshop.

---

## Bước 1 — Push repo lên GitHub (5 phút)

Repo local đã sẵn sàng ở `/Users/tommynguyen/Developer/work/SOY-SM-WORK/github-workshop`.

### Cách A: Dùng GitHub web (khuyến nghị cho lần đầu)

```bash
cd /Users/tommynguyen/Developer/work/SOY-SM-WORK/github-workshop

# Đã có git init ở local. Giờ tạo repo trên GitHub:
# 1. Vào https://github.com/new
# 2. Repository name: github-workshop
# 3. Description: "ASW internal GitHub collaboration workshop"
# 4. Visibility: Public (nếu muốn show portfolio) hoặc Private (nếu nội bộ)
# 5. KHÔNG tick "Add README" / "Add .gitignore" (đã có sẵn local)
# 6. Click "Create repository"

# Sau khi tạo xong, chạy:
git remote add origin https://github.com/thien-soy/github-workshop.git
git branch -M main
git add .
git commit -m "chore: initial workshop repo setup"
git push -u origin main
```

### Cách B: Dùng GitHub CLI (nếu đã cài `gh`)

```bash
cd /Users/tommynguyen/Developer/work/SOY-SM-WORK/github-workshop
gh repo create github-workshop --public --source=. --remote=origin --push
```

---

## Bước 2 — Add collaborators (3 phút)

Vào repo → **Settings → Collaborators → Add people**

Add 4 người:
- `liemsoy`
- `ngocsoyasw`
- `QuangSoyAgency`
- `anhsoyagency`

Role mặc định: **Write** (đủ quyền push branch + mở PR).

---

## Bước 3 — Branch protection cho `main` (5 phút)

Vào **Settings → Branches → Add branch protection rule**:

| Setting                        | Value                              |
|--------------------------------|------------------------------------|
| Branch name pattern            | `main`                             |
| Require a pull request before merging | ✅ ON                          |
| Require approvals              | ✅ ON, minimum **1 approval**      |
| Dismiss stale pull request approvals when new commits are pushed | ✅ ON |
| Require review from Code Owners | ❌ OFF (chưa cần)                 |
| Require status checks to pass before merging | ❌ OFF (no CI chưa)  |
| Require conversation resolution before merging | ✅ ON (optional, recommended) |
| Include administrators          | ❌ OFF (anh vẫn push được nếu cần) |
| Allow force pushes             | ❌ OFF                              |
| Allow deletions                | ❌ OFF                              |

Click **Create** → giờ `main` đã protected, ai cũng phải qua PR + review.

---

## Bước 4 — Tạo 4 issue mẫu cho team (5 phút)

Vào **Issues → New issue** → chọn template:

| # | Title                                         | Template        | Assignee         |
|---|-----------------------------------------------|-----------------|------------------|
| 1 | `[FEAT] Add intro page for liemsoy`            | Feature Request | `liemsoy`        |
| 2 | `[FEAT] Add intro page for ngocsoyasw`          | Feature Request | `ngocsoyasw`     |
| 3 | `[FEAT] Add intro page for QuangSoyAgency`      | Feature Request | `QuangSoyAgency` |
| 4 | `[FEAT] Add intro page for anhsoyagency`        | Feature Request | `anhsoyagency`   |

Apply label `good first issue` cho cả 4 để newbie biết bắt đầu từ đâu.

---

## Bước 5 — Verify trước buổi học (5 phút)

Self-test checklist:

- [ ] Repo public/private đúng setting
- [ ] Có thể clone về máy khác (`git clone https://github.com/thien-soy/github-workshop.git` trên máy khác để test)
- [ ] 4 collaborators đã được invite và accept
- [ ] `main` đã protected
- [ ] 4 issue đã tạo và assignee đúng
- [ ] Tạo 1 PR test → verify template load đúng → close PR test (không merge)

---

## Bước 6 — Trong buổi workshop (theo WORKSHOP.md)

Mở file `WORKSHOP.md` và follow từng phần. File đã chia sẵn 7 phần + thời lượng.

---

## 📞 Troubleshooting nhanh cho mentor

| Vấn đề                                       | Giải pháp                                                                 |
|----------------------------------------------|---------------------------------------------------------------------------|
| Học viên k thấy repo                        | Chưa accept invite → check email (kể cả spam)                            |
| `git push` báo auth fail                    | Hướng dẫn dùng Personal Access Token (xem WORKSHOP.md phần Troubleshooting) |
| `main` bị lock, không push được             | Đúng rồi → đó là branch protection hoạt động → phải qua PR               |
| Conflict không ai biết resolve              | Pair-work với mentor 5 phút, dùng VSCode merge editor                    |
| Học viên commit sai author                  | `git commit --amend --author="..."` rồi `git push --force`                |

---

**Estimated total setup time:** ~25 phút
**Workshop duration:** ~2.5 giờ
