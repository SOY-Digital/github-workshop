# 🌱 GitHub Workshop — ASW Team

> Workshop nội bộ ASW để làm quen với **GitHub collaboration workflow** (issues → branches → PRs → reviews → merge).
> Repo được thiết kế 100% bằng Markdown — không cần cài môi trường code, không cần IDE.
> Tập trung 100% vào kỹ năng làm việc nhóm trên GitHub.

---

## 👥 Team & GitHub Handles

| Thành viên        | GitHub user        | Role trong repo                  |
|-------------------|--------------------|----------------------------------|
| Tommy (mentor)    | `thien-soy`        | Repo owner, review & merge       |
| Liem Bui           | `liemsoy`          | Contributor                      |
| Ngoc Le            | `ngocsoyasw`       | Contributor                      |
| Quang Hoang        | `QuangSoyAgency`   | Contributor                      |
| Anh Le             | `anhsoyagency`     | Contributor                      |

---

## 🎯 Mục tiêu workshop

Sau 2-3 giờ, mỗi người sẽ:

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
git checkout -b feat/<ten-cua-ban>-intro

# 3. Sửa file team-pages/<github-user>.md (xem phần Bài tập bên dưới)

# 4. Commit & push
git add .
git commit -m "feat: add intro page for <ten-cua-ban>"
git push -u origin feat/<ten-cua-ban>-intro

# 5. Mở Pull Request trên GitHub → chờ review → merge
```

Chi tiết từng bước xem **[WORKSHOP.md](./WORKSHOP.md)**.

---

## 📚 Tài liệu

| File                                                       | Mô tả                                                    |
|------------------------------------------------------------|----------------------------------------------------------|
| [WORKSHOP.md](./WORKSHOP.md)                               | Hướng dẫn step-by-step cho toàn bộ buổi workshop        |
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

## 📞 Liên hệ

Có thắc mắc → mở issue với label `question`, hoặc ping Tommy trên Slack/Teams.
