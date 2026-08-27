# Bài tập 1 — Personal Intro Page (20 phút)

**Mục tiêu:** Làm quen với toàn bộ flow: clone → branch → commit → push → PR → review → merge.

## Yêu cầu

Mỗi thành viên tạo file `team-pages/<github-user>.md` chứa:
- Tên + GitHub user
- Role trong team
- 1 dòng giới thiệu
- 1 thứ muốn học ở workshop

## Step-by-step

```bash
# 1. Sync main
git checkout main && git pull origin main

# 2. Tạo branch riêng
git checkout -b feat/<github-user>-intro

# 3. Copy template và sửa
cp team-pages/_template.md team-pages/<github-user>.md
# Sửa file bằng editor yêu thích

# 4. Stage + commit
git add team-pages/<github-user>.md
git commit -m "feat: add intro page for <github-user>"

# 5. Push
git push -u origin feat/<github-user>-intro

# 6. Mở PR trên GitHub UI
# 7. Add 1 reviewer khác trong team
# 8. Chờ approve → merge
```

## Done khi

- [ ] File `<github-user>.md` đã có trong `team-pages/`
- [ ] PR đã merged vào `main`
- [ ] Đã có ít nhất 1 người review PR của bạn
- [ ] Bạn đã review PR của ít nhất 1 người khác
- [ ] Local đã sync với `main` mới nhất

## Stretch goal 🌟

- Thêm emoji header cho sinh động
- Nhúng ảnh avatar (dùng URL từ GitHub profile)
- Thêm section "Goals năm 2026"
