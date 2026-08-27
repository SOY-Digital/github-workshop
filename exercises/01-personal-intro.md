# Bài tập 1 — Trang giới thiệu của bạn (20 phút)

Bài này đi qua trọn vòng: clone → branch → commit → push → PR → review → merge. Làm xong là bạn đã nắm 80% flow làm việc nhóm.

## Việc cần làm

Tạo file `team-pages/<github-user>.md` (ví dụ `liemsoy.md`) chứa: tên và github user, vai trò trong team, một dòng giới thiệu, một thứ bạn muốn học sau khóa này.

## Từng bước

```bash
# về main mới nhất
git checkout main && git pull origin main

# branch riêng của bạn
git checkout -b feat/<github-user>-intro

# copy template rồi sửa nội dung
cp team-pages/_template.md team-pages/<github-user>.md     # macOS/Linux
# Windows PowerShell: Copy-Item team-pages/_template.md team-pages/<github-user>.md

# stage, commit, push
git add team-pages/<github-user>.md
git commit -m "feat: add intro page for <github-user>"
git push -u origin feat/<github-user>-intro
```

Rồi mở PR trên GitHub (bấm nút Compare & pull request trên banner vàng). Thêm reviewer là một bạn khác trong team. Đủ approval thì tự bấm Squash and merge.

Nếu có issue giao bài này cho bạn thì thêm `Closes #<số>` vào PR description để issue tự đóng.

## Xong khi nào

- File `<github-user>.md` đã nằm trong `team-pages/` trên main
- PR của bạn đã được merge, và đã có ít nhất một người review nó
- Bạn đã review PR của ít nhất một bạn khác
- Máy local đã pull main mới nhất về

## Làm thêm nếu muốn

- Nhúng avatar: lấy URL ảnh từ profile GitHub của bạn
- Thêm mục mục tiêu năm 2026
- Trang trí heading bằng emoji — bài này thôi nhé, repo khác người ta có thể không thích

## Lỗi hay gặp

Commit không có avatar của bạn trên GitHub: email git chưa khớp email GitHub. Xem lại Phần 0 của WORKSHOP.md.
