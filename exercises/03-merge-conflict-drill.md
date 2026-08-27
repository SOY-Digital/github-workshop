# Bài tập 3 — Merge Conflict Drill (20 phút)

**Mục tiêu:** Hết sợ merge conflict — tự tay tạo một conflict THẬT, đọc được markers, tự resolve.

> Bài này làm **một mình**, 100% trên máy local — không cần đợi ai review hay phối hợp giờ giấc.

## Conflict xảy ra khi nào?

Khi 2 branch cùng sửa **cùng 1 dòng** từ cùng một điểm xuất phát, git không biết giữ bên nào → conflict. Drill này mô phỏng đúng tình huống thực tế: bạn và một đồng nghiệp cùng sửa 1 file song song.

## Drill

File drill đã có sẵn trong repo: [`exercises/conflict-target.md`](./conflict-target.md). Tất cả thay đổi chỉ ở **dòng 3** của file đó.

```bash
# Bước 1 — mô phỏng "đồng nghiệp": branch khác sửa dòng 3
git checkout main && git pull
git checkout -b chore/other-rule
# SỬA DÒNG 3: thay <VIẾT RULE...> bằng 1 rule (VD: "3. Code xong phải tự test trước khi mở PR")
git add exercises/conflict-target.md
git commit -m "docs: add rule 3 from other branch"

# Bước 2 — branch "của bạn": cũng sửa dòng 3, từ CÙNG main (chưa có rule trên)
git checkout main
git checkout -b docs/my-rule
# SỬA DÒNG 3 bằng rule KHÁC của bạn (VD: "3. Không bao giờ push thẳng vào main")
git add exercises/conflict-target.md
git commit -m "docs: add my rule 3"

# Bước 3 — "đồng nghiệp" merge trước: gộp rule của họ vào main LOCAL
git checkout main
git merge chore/other-rule      # chạy sạch (không ai khác sửa gì)

# Bước 4 — giờ merge main vào branch của bạn → CONFLICT
git checkout docs/my-rule
git merge main
# Git sẽ báo:
# CONFLICT (content): Merge conflict in exercises/conflict-target.md
# Automatic merge failed; fix conflicts and then commit the result.
```

## Đọc conflict markers

Mở `exercises/conflict-target.md`, bạn sẽ thấy:

```text
<<<<<<< HEAD
3. Không bao giờ push thẳng vào main      ← phía BẠN (branch hiện tại = HEAD)
=======
3. Code xong phải tự test trước khi mở PR  ← phía main (đồng nghiệp merge trước)
>>>>>>> main
```

Cách đọc:

| Marker | Nghĩa |
|---|---|
| `<<<<<<< HEAD` ... `=======` | thay đổi trên **branch của bạn** |
| `=======` ... `>>>>>>> main` | thay đổi từ **main** mà bạn đang gộp vào |

## Resolve

1. Quyết định giữ gì — 3 lựa chọn:
   - Giữ của bạn, xóa của main
   - Giữ của main, xóa của bạn
   - **Gộp cả hai** thành dòng 3 + dòng 4 (khuyến nghị — thực tế hay gặp nhất)
2. Sửa file cho ra nội dung cuối, **xóa sạch cả 3 markers**
3. Hoàn tất merge:

```bash
git status                        # file conflict hiện "both modified"
# (sửa file tại đây nếu chưa sửa)
git add exercises/conflict-target.md
git commit                        # giữ nguyên message merge mặc định, chỉ cần save & thoát editor
```

> Nếu vim hiện ra và bạn không thoát được: gõ `:wq` rồi Enter (ghi & thoát).

## Push kết quả (tùy chọn nhưng nên làm)

```bash
git push -u origin docs/my-rule
# Mở PR trên GitHub, trong description ghi rõ: "Bài tập 3 — conflict drill, đã resolve, gộp 2 rules"
# Tommy sẽ review như thường lệ — không gấp, làm bài khác trong lúc chờ.
```

## Done khi

- [ ] Đã tự tạo được conflict ở Bước 4 (git báo CONFLICT)
- [ ] Giải thích được 3 markers `<<<<<<<`, `=======`, `>>>>>>>` nghĩa là gì
- [ ] File sau resolve KHÔNG còn marker nào, có ít nhất 2 rules (dòng 3, 4)
- [ ] `git log --oneline --graph -6` hiện merge commit hình chữ V

## Dọn dẹp sau drill (giữ main sạch cho người sau)

```bash
git checkout main && git pull
git branch -D chore/other-rule docs/my-rule   # xoá branch drill local
# KHÔNG push main local (đã gộp rule ở bước 3) — để nguyên, GitHub main là chuẩn
```

> ⚠️ Bước 3 đã gộp rule vào **main local** của bạn. Khi `git pull` sau này, nếu remote main không có rule đó (Tommy không merge PR drill), git sẽ báo lệch — cứ để local main đuổi theo remote: nếu gặp thông báo, chạy `git pull` rồi chọn giữ bản remote (revert local bằng `git reset --hard origin/main` — an toàn vì drill chỉ là tập).

## Mẹo

- Đây là bài **khó nhất** của lộ trình — mất 2-3 lần làm mới nhớ là bình thường.
- Conflict thật trong dự án: luôn đọc kỹ CẢ HAI phía trước khi chọn, không ưu tiên "của mình luôn đúng".
- VSCode có merge editor trực quan: click "Resolve in Merge Editor" khi git báo conflict.
