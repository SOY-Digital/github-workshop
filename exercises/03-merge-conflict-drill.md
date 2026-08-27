# Bài tập 3 — Tự tạo merge conflict rồi tự gỡ (20 phút)

Conflict là thứ khiến người mới sợ git nhất. Cách hết sợ là làm cho ra: bài này bạn sẽ tự tay tạo một conflict thật trên máy mình, đọc hiểu nó muốn nói gì, rồi gỡ lấy. Làm một mình, không cần ai phối hợp.

## Conflict xảy ra khi nào

Hai branch cùng sửa một dòng từ cùng một điểm xuất phát. Lúc merge, git không biết giữ bên nào, nên nó đưa quyết định lại cho bạn. Bài này mô phỏng đúng tình huống thật: bạn và một đồng nghiệp cùng sửa một file song song.

File để luyện có sẵn: [conflict-target.md](./conflict-target.md). Mọi thay đổi chỉ xảy ra ở dòng 3.

## Tạo conflict

```bash
# bước 1 — đóng vai "đồng nghiệp": một branch khác sửa dòng 3
git checkout main && git pull
git checkout -b chore/other-rule
# sửa dòng 3: thay phần <...> bằng một rule, ví dụ "3. Code xong phải tự test trước khi mở PR"
git add exercises/conflict-target.md
git commit -m "docs: add rule 3 from other branch"

# bước 2 — đóng vai "bạn": cũng sửa dòng 3, nhưng từ main (chưa có rule trên)
git checkout main
git checkout -b docs/my-rule
# sửa dòng 3 bằng rule KHÁC của bạn, ví dụ "3. Không bao giờ push thẳng vào main"
git add exercises/conflict-target.md
git commit -m "docs: add my rule 3"

# bước 3 — "đồng nghiệp" merge trước: đưa rule của họ vào main (bản local)
git checkout main
git merge chore/other-rule        # merge sạch, không sao cả

# bước 4 — giờ merge main vào branch của bạn
git checkout docs/my-rule
git merge main
```

Bước 4 git sẽ báo:

```
CONFLICT (content): Merge conflict in exercises/conflict-target.md
Automatic merge failed; fix conflicts and then commit the result.
```

Đó chính là điều bạn muốn tạo ra.

## Đọc conflict

Mở `exercises/conflict-target.md`:

```
<<<<<<< HEAD
3. Không bao giờ push thẳng vào main        <- phía bạn (branch hiện tại)
=======
3. Code xong phải tự test trước khi mở PR   <- phía main (đồng nghiệp merge trước)
>>>>>>> main
```

Ba marker: mọi thứ giữa `<<<<<<< HEAD` và `=======` là của bạn, giữa `=======` và `>>>>>>> main` là của phía kia. Git không chọn hộ bạn — nó chờ bạn quyết.

## Gỡ

Ba lựa chọn: giữ của bạn, giữ của họ, hoặc gộp cả hai. Thường thì gộp cả hai là đúng — hai người cùng có ý muốn sửa, chỉ là chưa biết về nhau. Giữ cả hai rules, biến thành dòng 3 và dòng 4.

Sửa file cho ra kết quả cuối, xóa sạch cả ba marker, rồi:

```bash
git status                                        # file hiện "both modified"
git add exercises/conflict-target.md
git commit                                        # giữ nguyên message merge mặc định
```

Nếu vim bật lên: gõ `:wq` rồi Enter.

## Push kết quả (nên làm)

```bash
git push -u origin docs/my-rule
```

Mở PR, ghi rõ trong description rằng đây là bài conflict drill và bạn đã gộp cả hai rules. Thiện sẽ review như thường lệ, không gấp — cứ làm tiếp phần khác trong lúc chờ.

## Xong khi nào

- Bước 4 git có báo CONFLICT (tức là bạn đã tạo đúng tình huống)
- Giải thích được ba marker nghĩa là gì mà không cần nhìn lại tài liệu
- File sau khi gỡ không còn marker nào, và có cả hai rules
- `git log --oneline --graph -6` hiện merge commit hình chữ V

## Dọn sau khi luyện

```bash
git checkout main
git branch -D chore/other-rule docs/my-rule
```

Lưu ý: bước 3 đã đưa rule "đồng nghiệp" vào main bản local của bạn, trong khi main trên GitHub không có. Gặp thông báo lệch khi pull sau này thì chạy `git reset --hard origin/main` để lấy main remote làm chuẩn — an toàn, vì đây chỉ là bài luyện.

## Vài lời

Đây là bài khó nhất của lộ trình, làm hai ba lần mới nhớ là bình thường. Khi gặp conflict thật trong dự án: đọc kỹ cả hai phía trước khi chọn, đừng mặc định phía mình luôn đúng. VSCode có merge editor trực quan — bấm "Resolve in Merge Editor" khi git báo conflict là thấy.
