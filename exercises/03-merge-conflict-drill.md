# Bài tập 3 — Merge Conflict Drill (20 phút)

**Mục tiêu:** Hết sợ merge conflict. Pair-work (2 người cùng sửa 1 file).

## Setup

Mentor tạo sẵn file `exercises/conflict-target.md` với nội dung:

```markdown
# Workshop Rules

1. Commit message phải theo Conventional Commits
2. Mỗi PR cần ít nhất 1 reviewer
3. <TODO: câu rule thứ 3 — người A sẽ điền>
4. <TODO: câu rule thứ 4 — người B sẽ điền>
```

## Pair assignment

| Cặp       | Người A sửa line 3        | Người B sửa line 4        |
|-----------|---------------------------|---------------------------|
| Pair 1    | Liêm (`liemsoy`)          | Ngọc (`ngocsoyasw`)       |
| Pair 2    | Quang (`QuangSoyAgency`)  | Anh (`anhsoyagency`)      |

## Flow

```bash
# Cả 2 cùng start từ main
git checkout main && git pull

# Người A
git checkout -b docs/pair1-rule3-liem
# Sửa line 3 trong conflict-target.md → commit → push → mở PR (CHƯA merge)

# Người B (làm song song)
git checkout -b docs/pair1-rule4-ngoc
# Sửa line 4 trong conflict-target.md → commit → push → mở PR (CHƯA merge)

# Ai mở PR sau sẽ gặp conflict khi merge → đây là phần drill
```

## Khi gặp conflict

Trong PR tab "Files changed" → click **"Resolve conflicts"** → sửa trực tiếp trên web editor, hoặc resolve local:

```bash
git checkout <branch-của-mình>
git fetch origin
git merge origin/main
# Mở file bị conflict, xóa markers <<<<<<< ======= >>>>>>>
# Giữ cả 2 thay đổi (hoặc chỉ 1, tùy case)
git add .
git commit -m "fix: resolve merge conflict in conflict-target.md"
git push
```

## Done khi

- [ ] Cả 2 PR đã merged
- [ ] File `conflict-target.md` có đủ 4 rules
- [ ] Hiểu được markers `<<<<<<<`, `=======`, `>>>>>>>`
- [ ] Merge commit hoặc re-commit hiển thị trong history

## Mentor note

Đây là bài **khó nhất** workshop. Đừng rush. Quan trọng là:
- Đọc kỹ conflict (xem ai thay đổi gì)
- Hỏi reviewer nếu không chắc nên giữ phần nào
- Commit message rõ ràng
