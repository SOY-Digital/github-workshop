# Bài tập 2 — Danh sách tài nguyên hay (25 phút)

Bài trước bạn học flow PR. Bài này thêm một thói quen của team chuyên nghiệp: mở issue trước khi làm, và xử lý feedback trong lúc review.

## Bối cảnh

Team muốn dựng một danh sách chung các tài nguyên đáng đọc: blog, tool, khóa học, sách. Mỗi người phụ trách một mảng:

| Mảng | Người phụ trách | File |
|---|---|---|
| Dev tools | `liemsoy` | `resources/dev-tools.md` |
| Learning | `ngocsoyasw` | `resources/learning.md` |
| Productivity | `QuangSoyAgency` | `resources/productivity.md` |
| Fun / Inspo | `anhsoyagency` | `resources/fun-inspo.md` |

Ai làm nhanh thì chọn mảng trước. Hai người muốn đổi mảng cho nhau thì trao đổi trong issue.

## Các bước

Bước 1: mở issue trước. Tab Issues, New issue, điền đại loại "[FEAT] Thêm danh sách dev tools — Liem". Issue là chỗ ghi lại việc cần làm và trao đổi, PR chỉ là chỗ giao kết quả.

Bước 2 đến 5:

```bash
# branch mới, đặt tên theo issue và mảng của bạn
git checkout main && git pull
git checkout -b feat/<github-user>-<category>

# tạo file, mỗi tài nguyên gồm: tên, link, một hai dòng vì sao đáng đọc
mkdir -p resources
# (soạn nội dung resources/<category>.md, tối thiểu 3 mục)

git add resources/<category>.md
git commit -m "feat: add favorite dev tools list"
git push -u origin feat/<github-user>-<category>
```

Bước 6: mở PR, trong description thêm `Closes #<số issue>` ở bước 1. Thêm reviewer là một bạn khác, có approval thì merge.

## Người review kiểm tra gì

Mỗi mục có đủ tên, link, lý do chưa. Link có sống không (bấm thử). Nội dung có đúng mảng không — danh sách dev tools mà toàn meme thì phải đổi mảng chứ không phải đổi tên file.

## Xong khi nào

- Issue mở trước, PR reference đúng issue bằng `Closes #X`
- File có tối thiểu 3 tài nguyên, đủ ba thành phần trên mỗi mục
- PR được merge, issue tự đóng theo

## Làm thêm nếu muốn

- Đánh giá sao cho từng mục (một đến năm sao, kiểu `***`)
- Gắn nhãn free/paid cho từng tài nguyên
- Link chéo giữa các file khi hai mảng có mục liên quan
