# 🤝 Contributing Guide

> Đọc file này TRƯỚC khi tạo Pull Request đầu tiên.

Repo này dùng workflow chuẩn của GitHub: **issue → branch → PR → review → merge**.

---

## 📌 Branch naming convention

| Prefix       | Dùng cho                                  | Ví dụ                          |
|--------------|-------------------------------------------|--------------------------------|
| `feat/`      | Tính năng mới, nội dung mới               | `feat/liemsoy-intro`           |
| `fix/`       | Sửa lỗi typo, sai thông tin               | `fix/readme-typo`              |
| `docs/`      | Chỉ sửa documentation                    | `docs/update-workshop-md`      |
| `chore/`     | Cleanup, đổi tên file, tooling           | `chore/remove-old-template`    |
| `refactor/`  | Tái cấu trúc không đổi behavior          | `refactor/reorganize-exercises`|

**Rule:** `<prefix>/<short-description-kebab-case>`. Không dấu cách, không uppercase, không ký tự đặc biệt.

---

## 💬 Commit message convention

Dùng [Conventional Commits](https://www.conventionalcommits.org/):

```
<type>(<scope>): <description>

[optional body]

[optional footer]
```

**Type:** `feat` | `fix` | `docs` | `style` | `refactor` | `test` | `chore`

**Ví dụ tốt:**

```bash
git commit -m "feat: add intro page for liemsoy"
git commit -m "fix: correct typo in WORKSHOP.md"
git commit -m "docs: add troubleshooting section"
git commit -m "chore: remove unused template file"
```

**Ví dụ XẤU (sẽ bị reject):**

```bash
git commit -m "update"
git commit -m "fix bug"
git commit -m "asdfasdf"
```

---

## 🔄 Pull Request process

1. **Tạo branch mới** từ `main` (không bao giờ push thẳng vào `main`)
2. **Commit nhỏ, focus:** 1 PR = 1 thay đổi logic
3. **Push branch** lên origin: `git push -u origin <branch-name>`
4. **Mở PR** trên GitHub → điền template đầy đủ
5. **Add reviewer:** chọn ít nhất 1 người trong team (không phải mình)
6. **Chờ review** → phản hồi comment → push fix nếu cần
7. **Merge** khi có ≥ 1 approval + CI xanh (nếu có)

**Một PR lý tưởng:**
- Dưới 200 dòng thay đổi (nếu nhiều hơn → chia nhỏ)
- Title rõ ràng, dùng conventional commit format
- Description có: Summary, Changes, How to test
- Có ít nhất 1 reference tới issue (nếu có)

---

## 🐛 Issues

Trước khi tạo issue mới:
1. Search existing issues để tránh duplicate
2. Chọn template phù hợp (Bug report / Feature request / Question)
3. Điền đầy đủ các field bắt buộc
4. Apply labels nếu biết

**Reference issue trong PR:**
- `Closes #12` → đóng issue khi merge
- `Refs #12` → link nhưng không tự đóng

---

## ✅ Review checklist (cho reviewer)

Khi review PR, check:

- [ ] Title + description rõ ràng
- [ ] Changes đúng scope của PR (không lẫn file unrelated)
- [ ] Không có typo, link hỏng, format lỗi
- [ ] Markdown render đúng (xem tab Preview)
- [ ] Nếu là `feat/`: giải thích được vì sao cần
- [ ] Comment mang tính xây dựng, không toxic

---

## 🚫 Những điều KHÔNG làm

- ❌ Push thẳng vào `main` (sẽ bị block bởi branch protection)
- ❌ Force push lên shared branch (`git push -f`)
- ❌ Commit file binary lớn (ảnh, PDF — dùng link thay thế)
- ❌ Merge PR của chính mình (phải có người khác review)
- ❌ Bỏ qua template khi mở PR/issue

---

Có thắc mắc? Mở issue với label `question` hoặc hỏi trong team channel.
