# Bài tập 2 — Favorite Resources List (25 phút)

**Mục tiêu:** Thực hành mở issue trước khi code, xử lý feedback trong PR review.

## Scenario

Team muốn xây dựng một **shared list** các tài nguyên hay (blog, tool, course, book) mà mỗi người recommend. Mỗi người phụ trách 1 category.

## Categories (nhận phần ngay khi bắt đầu bài — ai nhanh chọn trước)

| Category       | Owner             | File                              |
|----------------|-------------------|-----------------------------------|
| Dev tools      | `liemsoy`         | `resources/dev-tools.md`          |
| Learning       | `ngocsoyasw`      | `resources/learning.md`           |
| Productivity   | `QuangSoyAgency`  | `resources/productivity.md`       |
| Fun / Inspo    | `anhsoyagency`    | `resources/fun-inspo.md`          |

## Flow bắt buộc

```bash
# 1. Mở issue trước (track được conversation)
# GitHub UI → Issues → New issue → "Add favorite resources for <category>"

# 2. Tạo branch từ issue
# Ví dụ: issue #7 → branch: feat/liemsoy-dev-tools
git checkout main && git pull
git checkout -b feat/<github-user>-<category>

# 3. Tạo file + thêm tối thiểu 3 resources
mkdir -p resources
touch resources/<category>.md

# Format mỗi resource:
# - Tên
# - URL
# - 1-2 dòng mô tả tại sao hay

# 4. Commit + push + mở PR
# 5. Trong PR description: "Closes #7"
# 6. Add reviewer là bạn khác trong team → có approval → tự merge
```

## Review yêu cầu

Reviewer check:
- Format đúng chưa
- Resources có thật sự liên quan không (không spam)
- Có link hợp lệ không

## Done khi

- [ ] Đã mở issue trước khi code
- [ ] File `resources/<category>.md` có ≥ 3 resources
- [ ] PR có `Closes #X` để auto-close issue
- [ ] PR đã merged
- [ ] Issue đã tự động đóng sau khi merge

## Stretch goal 🌟

- Thêm emoji rating ⭐⭐⭐⭐⭐
- Sort theo category phụ (free/paid, beginner/advanced)
- Cross-link resources giữa các file
