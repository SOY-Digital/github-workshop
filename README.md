# 🌱 GitHub Workshop — ASW Team

> Lộ trình **tự học (self-study)** làm quen **GitHub collaboration workflow** (issues → branches → PRs → reviews → merge). Làm ở nhà, theo tốc độ riêng — mỗi phần có self-check, không cần chờ buổi học.
> Repo được thiết kế 100% bằng Markdown — không cần cài môi trường code, không cần IDE.
> Tập trung 100% vào kỹ năng làm việc nhóm trên GitHub.

---

## 👥 Team & GitHub Handles

| Thành viên        | GitHub user        | Role trong repo                  |
|-------------------|--------------------|----------------------------------|
| Tommy (maintainer) | `thien-soy`        | Repo owner, setup & review PR     |
| Liem Bui           | `liemsoy`          | Contributor                      |
| Ngoc Le            | `ngocsoyasw`       | Contributor                      |
| Quang Hoang        | `QuangSoyAgency`   | Contributor                      |
| Anh Le             | `anhsoyagency`     | Contributor                      |

---

## 🎯 Mục tiêu lộ trình

Sau ~2.5-3 giờ tự học, mỗi người sẽ:

1. ✅ Clone repo về máy, làm việc với `git` cơ bản
2. ✅ Tạo branch riêng, commit, push lên GitHub
3. ✅ Mở **Pull Request** đúng chuẩn (template, mô tả, link issue)
4. ✅ **Review** PR của người khác (comment, approve, request changes)
5. ✅ Merge PR và đồng bộ `main` về local
6. ✅ Xử lý **merge conflict** cơ bản

---

## 🚀 Bắt đầu nhanh (5 phút)

```bash
# 1. Clone repo (sau khi Tommy push lên GitHub)
git clone https://github.com/SOY-Digital/github-workshop.git
cd github-workshop

# 2. Tạo branch riêng của bạn
git checkout -b feat/<github-user>-intro   # VD: feat/liemsoy-intro

# 3. Sửa file team-pages/<github-user>.md (xem phần Bài tập bên dưới)

# 4. Commit & push
git add .
git commit -m "feat: add intro page for <github-user>"   # VD: feat: add intro page for liemsoy
git push -u origin feat/<github-user>-intro

# 5. Mở Pull Request trên GitHub → review chéo với bạn khác trong team → merge
```

Chi tiết từng bước xem **[WORKSHOP.md](./WORKSHOP.md)**.

---

## 📚 Tài liệu

| File                                                       | Mô tả                                                    |
|------------------------------------------------------------|----------------------------------------------------------|
| [WORKSHOP.md](./WORKSHOP.md)                               | Lộ trình self-study step-by-step (Phần 0 → 7)           |
| [CONTRIBUTING.md](./CONTRIBUTING.md)                       | Quy ước commit, branch, PR khi làm việc nhóm             |
| [exercises/](./exercises)                                  | Các bài tập thực hành (mỗi bài 15-20 phút)              |
| [team-pages/](./team-pages)                                | Trang giới thiệu cá nhân — output chính của bài 1        |

---

## 🛠️ Quy ước repo này

- **Default branch:** `main` (protected — không push trực tiếp)
- **Commit format:** [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `chore:`...)
- **Branch naming:** `feat/`, `fix/`, `docs/`, `chore/`
- **PR template:** tự động khi mở PR — phải fill đầy đủ
- **Review:** tối thiểu **1 approval** trước khi merge

---

## 📞 Hỗ trợ khi bị kẹt

Tự học không có nghĩa học một mình:
1. Mở issue label `question` trong repo này (khuyến nghị — kiến thức sẻ chia cho cả team)
2. Nhắn Tommy trên Slack nếu gấp
