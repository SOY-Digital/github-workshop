# Bài tập 3 — Merge Conflict Drill (20 phút)

**Mục tiêu:** Hết sợ merge conflict. Pair-work (2 người cùng sửa 1 file).

## Setup

File drill đã có sẵn trong repo: [`exercises/conflict-target.md`](./conflict-target.md). Cả 2 người trong pair **cùng sửa dòng số 3** (cùng 1 dòng → đảm bảo 100% conflict):

```markdown
# Workshop Rules

1. Commit message phải theo Conventional Commits
2. Mỗi PR cần ít nhất 1 reviewer
3. <VIẾT RULE CỦA BẠN VÀO DÒNG NÀY>   ← dòng 3, người A và người B CÙNG sửa dòng này
```

> Mỗi người tự nghĩ 1 rule riêng (VD: "3. Code xong phải tự test trước khi mở PR"). Hai nội dung khác nhau trên cùng 1 dòng = git không tự gộp được = conflict thật.

## Pair assignment

| Cặp       | Người A                            | Người B                            |
|-----------|------------------------------------|------------------------------------|
| Pair 1    | Liem Bui (`liemsoy`) — rule của A | Ngoc Le (`ngocsoyasw`) — rule của B |
| Pair 2    | Quang Hoang (`QuangSoyAgency`) — rule của A | Anh Le (`anhsoyagency`) — rule của B |

## Flow

```bash
# Cả 2 cùng start từ main
git checkout main && git pull

# Người A
git checkout -b docs/pair1-liem-rule
# SỬA DÒNG 3 trong exercises/conflict-target.md (thay TODO bằng rule của mình)
git add exercises/conflict-target.md
git commit -m "docs: add pair1 rule by liem"
git push -u origin docs/pair1-liem-rule
# Mở PR trên GitHub → CHƯA merge, chờ mentor bật đèn xanh

# Người B (làm song song với A, không đợi)
git checkout -b docs/pair1-ngoc-rule
# SỬA DÒNG 3 (cùng dòng với A) — thay TODO bằng rule KHÁC của mình
git add exercises/conflict-target.md
git commit -m "docs: add pair1 rule by ngoc"
git push -u origin docs/pair1-ngoc-rule
# Mở PR → CHƯA merge

# Mentor merge PR của người A trước
# → PR của người B ngay lập tức hiện "This branch has conflicts that must be resolved"
# → Đây là phần drill chính
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
