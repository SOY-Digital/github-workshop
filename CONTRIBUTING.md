# Đóng góp vào repo này

Workflow của repo: issue → branch → pull request → review → merge. File này quy ước cụ thể từng bước. Đọc một lần trước khi mở PR đầu tiên là đủ.

## Đặt tên branch

| Prefix | Dùng cho | Ví dụ |
|---|---|---|
| `feat/` | nội dung mới | `feat/liemsoy-intro` |
| `fix/` | sửa lỗi, sai thông tin | `fix/readme-typo` |
| `docs/` | chỉ đụng documentation | `docs/update-workshop` |
| `chore/` | dọn dẹp, đổi tên file | `chore/remove-old-template` |
| `refactor/` | tái cấu trúc, không đổi hành vi | `refactor/reorganize-exercises` |

Format: `prefix/mô-tả-ngắn-kebab-case`. Không dấu cách, không chữ hoa.

## Commit message

Theo [Conventional Commits](https://www.conventionalcommits.org/): `type: mô tả ngắn`. Type hay dùng là `feat`, `fix`, `docs`, `chore`, `refactor`.

Tốt: `feat: add intro page for liemsoy`.

Tệ: `update`, `fix bug`, `asdfasdf`. Reviewer sẽ phải hỏi lại "sửa gì thế?", và PR nằm đó.

Mẹo viết nhanh: message chính là câu trả lời cho "PR này làm gì, nếu chỉ được nói một dòng?"

## Quy trình pull request

1. Branch mới từ `main`. Không bao giờ làm việc trực tiếp trên `main` — cũng chẳng làm được, nó được bảo vệ.
2. Commit nhỏ, mỗi commit một việc.
3. Push branch: `git push -u origin <branch-name>`.
4. Mở PR trên GitHub, điền template cho đủ.
5. Thêm reviewer là một bạn trong team.
6. Có comment thì trả lời; cần sửa thì push tiếp commit lên cùng branch.
7. Đủ một approval thì squash merge.

Một PR nên dưới 200 dòng diff. Nhiều hơn thì chia nhỏ — PR to người ta ngại review, và review vội thì Reviewer bỏ sót.

## Issue

Trước khi mở issue, search xem đã có ai hỏi chưa. Chọn đúng template (Báo lỗi, Đề xuất, Hỏi) và điền đủ các mục. Gắn label nếu biết label nào hợp.

Liên kết issue với PR: `Closes #12` thì issue tự đóng khi merge; `Refs #12` thì chỉ link, không đóng.

## Khi review PR của người khác

- Title và mô tả có nói rõ PR làm gì không
- Thay đổi có lẫn file không liên quan không
- Có typo, link chết, format hỏng không
- Markdown có render đúng không (xem Preview)
- Nếu là `feat/`: tác giả giải thích được vì sao cần thêm không

Comment để người viết sửa được, không phải để thể hiện. "Tên file nên là X vì quy ước ở CONTRIBUTING" hữu ích hơn "sai tên file".

## Những điều tránh

- Push thẳng vào `main` — branch protection sẽ chặn, đó là chủ đích.
- `git push -f` lên branch mà người khác cũng đang làm.
- Commit file nặng (ảnh, PDF) — dùng link thay vì nhét file vào repo.
- Merge PR của mình khi chưa có ai approve.
- Mở PR mà bỏ trống template.
