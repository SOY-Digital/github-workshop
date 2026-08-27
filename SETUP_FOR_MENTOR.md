# Setup & vận hành — dành cho Thiện

Repo này là tài liệu tự học: các bạn tự làm theo WORKSHOP.md ở nhà, review chéo nhau. Mình (người viết file này) chỉ setup một lần trước khi giao, sau đó vận hành nhẹ nhàng: review PR, trả lời issue, đo tiến độ.

## Trạng thái (cập nhật 2026-08-27)

- Repo live tại https://github.com/SOY-Digital/github-workshop, thuộc org SOY-Digital
- Invite collaborators: đã gửi đủ 4. `anhsoyagency` và `ngocsoyasw` đã accept. `liemsoy` và `QuangSoyAgency` chưa — nhắc họ check mail (kể cả spam). Accept xong thì họ vào issue #1 và #3 tự self-assign
- Merge settings: chỉ squash, auto-merge bật, tự xóa branch sau merge (đã set qua API)
- Branch protection `main`: cần 1 approval, dismiss stale reviews, yêu cầu resolve conversation, admin không bị chặn
- Issue giao bài: #1 đến #4 đã tạo, label `good first issue`. #1 và #3 chưa assign được vì chủ nhân chưa accept invite
- Đã verify bằng PR test #5: merge bị chặn đúng khi thiếu approval, auto-merge nhận method squash, PR test đã đóng và dọn branch. Clone ẩn danh cũng ổn

Còn lại một việc: nhắc hai bạn chưa accept invite.

## Phần A — đã làm rồi, giữ đây để đối chiếu

**Invite collaborators.** Settings, Collaborators and teams, Add people, thêm cả 4 với role Write. Muốn quản tập trung thì lập team trong org (Settings của org, Teams) rồi add team vào repo — làm sau cũng được, không gấp.

**Merge settings.** Settings, General, Pull Requests: chỉ để Allow squash merging, bật Automatically delete head branches. Học viên được hướng dẫn bấm nút Squash and merge, settings này làm cho nút đó là lựa chọn duy nhất.

**Bảo vệ main.** Settings, Branches, rule cho `main`: require PR trước khi merge, cần 1 approval, dismiss stale approvals, require conversation resolution. Không bật "Include administrators" để còn sửa gấp trực tiếp khi cần.

**Issue giao bài.** Bốn issue, mỗi bạn một issue tên `[FEAT] Add intro page for <user>`, label `good first issue`, assign cho đúng người.

**Verify trước khi giao.** Mở một PR thử: template load đúng, chỉ có nút squash, merge không approval bị chặn. Đóng PR thử, xóa branch. Clone từ máy khác không có credential — được.

## Phần B — vận hành hàng tuần, chừng 15 đến 30 phút

| Việc | Nhịp | Cách làm |
|---|---|---|
| Review PR đang treo | 1-2 lần/tuần | Tab Pull requests, lọc Awaiting your review. Học viên đủ approval chéo là tự merge được, mình chỉ approve hoặc góp ý |
| Trả lời issue `question` | trong ngày | Tab Issues, sort mới nhất. Khuyến khích các bạn trả lời nhau trước, mình vào chốt sau |
| Nhìn tiến độ | tuần một lần | Insights, Contributors, đếm PR merged của mỗi bạn. Ai im lặng quá một tuần thì nhắn riêng hỏi có kẹt ở đâu không |
| Dọn branch dư | tháng một lần | Tab Branches, xóa các branch drill `docs/my-rule` cũ |
| Ghi nhận hoàn thành | khi có issue "Hoàn thành lộ trình" | Reaction và lời chúc, ghi lại để tính cho phần nâng cao (gh CLI, Actions) |

## Khi có sự cố

| Tình huống | Cách xử lý |
|---|---|
| Bạn ấy không thấy repo | Chưa accept invite. Check mail, kể cả spam |
| Push bị auth fail | Trỏ họ tới mục "Xử lý lỗi thường gặp" cuối WORKSHOP.md: PAT hoặc SSH |
| Commit không có avatar | Email git chưa khớp email GitHub. WORKSHOP.md Phần 0 giải thích kỹ |
| Conflict drill không nổ conflict | Chắc chắn họ sửa hai dòng khác nhau thay vì cùng dòng 3. Bài tập viết rõ "cùng sửa dòng 3" |
| Commit sai author | `git commit --amend --author="Tên <email>"` rồi `git push --force-with-lease` |
| Ai đó merge nhầm vào main | `git revert <sha>` qua PR. Coi như thêm một khái niệm mới để dạy |

## Khi giao repo

Gửi các bạn một đoạn đại loại thế này:

> Mọi người ơi, mình mới dựng repo github-workshop trong org SOY-Digital để cả team làm quen GitHub. Vào repo, mở file WORKSHOP.md, làm từ Phần 0, mỗi phần có mục tự kiểm tra. Tự làm theo tốc độ riêng, review chéo nhau. Kẹt thì mở issue label question, hoặc nhắn mình. Không cần chờ ai.

Xong. Từ đó repo tự chạy.
