# GitHub Workshop — team ASW

Repo này là tài liệu tự học làm việc nhóm trên GitHub: issue, branch, pull request, review, merge. Toàn bộ là Markdown, không cần cài môi trường ngoài git. Làm ở nhà, theo tốc độ riêng của mỗi người.

## Team

| Người | GitHub | Vai trò |
|---|---|---|
| Thiện | `thien-soy` | maintainer, review PR |
| Liem Bui | `liemsoy` | contributor |
| Ngoc Le | `ngocsoyasw` | contributor |
| Quang Hoang | `QuangSoyAgency` | contributor |
| Anh Le | `anhsoyagency` | contributor |

## Học xong bạn sẽ làm được gì

- Clone repo, tạo branch, commit, push
- Mở pull request đúng template, mô tả để người review không phải đoán
- Review PR cho người khác: comment, approve, request changes
- Merge PR và đồng bộ `main` về máy
- Tự tay gỡ một merge conflict

Tổng thời gian khoảng 2.5–3 tiếng nếu làm liền mạch. Chia nhỏ nhiều buổi cũng được, mỗi phần kết thúc ở chỗ an toàn, không mất tiến độ.

## Bắt đầu

Mở [WORKSHOP.md](./WORKSHOP.md), làm tuần tự từ Phần 0. Nếu bạn đã quen git và chỉ muốn nhảy vào:

```bash
git clone https://github.com/SOY-Digital/github-workshop.git
cd github-workshop

git checkout -b feat/<github-user>-intro        # ví dụ: feat/liemsoy-intro

# tạo team-pages/<github-user>.md từ _template.md, sửa nội dung, rồi:

git add .
git commit -m "feat: add intro page for <github-user>"
git push -u origin feat/<github-user>-intro

# mở PR trên GitHub, nhờ một bạn khác review, có approval thì squash merge
```

Lần đầu tiên dùng git thì đừng bắt đầu từ đây — làm theo WORKSHOP.md từ đầu, sẽ nhanh hơn là tự mò và sai.

## Tài liệu trong repo

- [WORKSHOP.md](./WORKSHOP.md) — lộ trình tự học, Phần 0 đến Phần 7
- [CONTRIBUTING.md](./CONTRIBUTING.md) — quy ước branch, commit, PR của repo này
- [exercises/](./exercises) — ba bài tập, khó dần đều
- [team-pages/](./team-pages) — trang giới thiệu của từng người, kết quả của bài tập 1

Ba quy tắc cần biết trước khi bắt đầu: `main` được bảo vệ nên không push thẳng được, commit theo Conventional Commits, mỗi PR cần ít nhất một approval trước khi merge.

## Bị kẹt thì sao

Mở issue với label `question` — hỏi chỗ công khai thì cả team cùng được học. Gấp thì nhắn Thiện qua Slack. Tự học không có nghĩa là học một mình.
