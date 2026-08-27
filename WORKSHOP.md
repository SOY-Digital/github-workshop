# Tự học GitHub workflow

Tài liệu này dành cho các bạn lần đầu làm việc trên GitHub theo nhóm. Làm tuần tự từ Phần 0. Mỗi phần có mục "xong khi nào" để tự kiểm tra trước khi chuyển tiếp. Không ai giục — nhanh chậm tùy bạn — nhưng đừng bỏ phần nào.

Nếu làm liền mạch thì hết khoảng 2.5 đến 3 tiếng. Chia nhiều buổi cũng được.

Bị kẹt thì mở issue label `question` (Phần 7 dạy cách hỏi cho hiệu quả), hoặc nhắn Thiện qua Slack nếu gấp. Không có câu hỏi ngốc, chỉ có câu hỏi thiếu thông tin.

## Phần 0 — Chuẩn bị (15 phút)

Cài git nếu chưa có: macOS chạy `xcode-select --install`, Windows tải ở git-scm.com, Linux `apt install git`.

Rồi cấu hình danh tính:

```bash
git config --global user.name "Liem Bui"          # tên hiển thị của bạn
git config --global user.email "liem@asw.global"  # email tài khoản GitHub của bạn
```

Phần `user.name` là tên hiển thị, ghi gì cũng được. Phần `user.email` thì phải khớp với email của tài khoản GitHub bạn — đăng nhập github.com, vào Settings, Emails để xem.

Vì sao email lại quan trọng đến vậy: GitHub nhận diện commit thuộc về ai qua email, không phải qua tên. Email sai thì commit vẫn push lên được bình thường, nhưng nó không có avatar của bạn và không được tính vào contributions. Đây là lỗi người mới mắc nhiều nhất, và nó âm thầm đến mức có người vài tuần sau mới phát hiện.

Không muốn lộ email thật? Bật "Keep my email addresses private" trong Settings, Emails rồi dùng địa chỉ dạng `12345678+liemsoy@users.noreply.github.com` — GitHub hiện sẵn trong trang đó, copy được.

Kiểm tra lại đã cấu hình đúng chưa:

```bash
git config --global user.name
git config --global user.email
git --version
```

Cuối cùng, chắc chắn bạn đã nhận mail mời vào tổ chức SOY-Digital và bấm Accept (nhớ kiểm tra cả mục spam). Chưa thấy mail thì nhắn Thiện gửi lại.

Xong khi nào: `git --version` chạy được, email khớp GitHub, invite đã accept.

## Phần 1 — Làm quen màn hình GitHub (10 phút)

Mở repo trên trình duyệt và bấm lần lượt qua các tab:

| Tab | Dùng để làm gì |
|---|---|
| Code | xem file, đọc source |
| Issues | đặt câu hỏi, báo lỗi, đề xuất |
| Pull requests | xem và review thay đổi trước khi merge |
| Actions | CI/CD — khóa này chưa dùng đến |
| Settings | phân quyền, bảo vệ branch (chỉ người quản lý thấy) |
| Insights, Contributors | ai đóng góp bao nhiêu |

Sau đó mở một dự án lớn bất kỳ — `facebook/react` chẳng hạn — vào tab Pull requests, chọn một PR và nhìn ba chỗ: Conversation, Commits, Files changed khác nhau ra sao. Chưa hiểu hết cũng không sao, để mắt vào là được.

Xong khi nào: phân biệt được Issues với Pull requests, và biết chỗ nào để xem diff của một PR.

## Phần 2 — Clone repo về máy (10 phút)

```bash
git clone https://github.com/SOY-Digital/github-workshop.git
cd github-workshop

git status
git branch -a
git log --oneline -10

# mở repo bằng editor bạn thích
code .            # VSCode
open README.md    # macOS; Windows dùng: start README.md
```

Bài tự kiểm tra, trả lời không nhìn lại:

1. Branch mặc định của repo là gì?
2. Repo có bao nhiêu file `.md`?
3. Commit mới nhất nói gì?

<details>
<summary>Đáp án</summary>

1. `main` — và nó đang được bảo vệ.
2. Đếm bằng `find . -name "*.md" -not -path "./.git/*" | wc -l`, hoặc mở tab Code trên GitHub.
3. `git log --oneline -1` hiện SHA ngắn kèm message.

</details>

Xong khi nào: trả lời được cả ba câu mà không phải đoán.

## Phần 3 — Branch và commit đầu tiên (20 phút)

Phần này chính là [bài tập 1](./exercises/01-personal-intro.md). Mục tiêu: tạo file `team-pages/<github-user>.md` trên branch riêng rồi push lên.

```bash
# 1. về main và lấy mới nhất
git checkout main
git pull origin main

# 2. branch riêng, đặt tên theo github user của bạn
git checkout -b feat/liemsoy-intro

# 3. copy template và sửa nội dung
cp team-pages/_template.md team-pages/liemsoy.md        # macOS/Linux
# Windows PowerShell: Copy-Item team-pages/_template.md team-pages/liemsoy.md

# trong file, điền: tên, role, github user,
# một dòng giới thiệu, một thứ muốn học được sau khóa này

# 4. xem lại mình vừa sửa gì
git diff

# 5. stage và commit
git add team-pages/liemsoy.md
git commit -m "feat: add intro page for liemsoy"

# 6. push branch lên GitHub
git push -u origin feat/liemsoy-intro
```

Gặp lỗi authentication thì xuống mục [Xử lý lỗi thường gặp](#xử-lý-lỗi-thường-gặp) cuối file.

Xong khi nào: branch của bạn hiện trên GitHub (tab Code, dropdown branch), và commit có avatar của bạn. Commit mà không có avatar nghĩa là email sai — quay lại Phần 0 đọc lại phần email.

## Phần 4 — Mở pull request (15 phút)

Push xong, vào repo trên GitHub sẽ thấy banner vàng với nút **Compare & pull request**. Bấm vào.

- Title: giữ nguyên commit message, ví dụ `feat: add intro page for liemsoy`.
- Description: template tự load sẵn, điền cho đủ. Mục How to test ghi đại loại `git checkout feat/liemsoy-intro && cat team-pages/liemsoy.md`.
- Reviewers bên phải: chọn một bạn khác trong team.
- Labels: `documentation`.

Bấm Create pull request. PR lúc này đang chờ review — đó là trạng thái bình thường, không phải lỗi.

Xong khi nào: PR mở thành công, hiện "Awaiting review", template đã điền đủ.

## Phần 5 — Review PR cho người khác (15 phút)

Nguyên tắc của repo này: mở một PR thì review một PR của bạn khác. Bốn người mà ai cũng giữ nguyên tắc này thì không PR nào phải nằm chờ.

Vào PR mà bạn được thêm làm reviewer, mở tab **Files changed**:

- Đọc từng dòng thay đổi. Có gì muốn nói thì hover vào dòng, bấm dấu **+** để comment.
- Chốt bằng nút **Review changes** góc phải, ba lựa chọn: **Comment** (góp ý, không chặn), **Approve** (đồng ý merge), **Request changes** (phải sửa trước khi merge).

Comment hữu ích trông như thế nào: "Mục X hay, nhưng tên file nên là...", "Link này 404 nè", "Ý bạn ở đây là...?". Comment chỉ gõ "ok" thì người viết chẳng biết sửa gì.

Khi chính PR của bạn được review:

- Có comment thì trả lời trong thread. Cần sửa thì push commit mới lên cùng branch, PR tự cập nhật.
- Bị Request changes thì sửa xong push lên, rồi bấm **Re-request review** để người review xem lại.
- Đủ approval thì tự bấm **Squash and merge**. Repo cấu hình chỉ cho squash và tự xóa branch sau merge, không cần chờ ai cho phép.

```bash
# sau khi merge, dọn máy
git checkout main
git pull origin main
git branch -d feat/liemsoy-intro
```

Xong khi nào: bạn đã review (comment hoặc approve) ít nhất một PR của bạn khác, và PR của bạn đã được merge.

## Phần 6 — Merge conflict (20 phút)

Đây là phần khiến người mới sợ git nhất, nên nó có hẳn một bài tập riêng: [bài tập 3](./exercises/03-merge-conflict-drill.md). Bạn sẽ tự tạo một conflict thật trên máy mình, đọc hiểu các marker, rồi tự gỡ. Làm một mình, không cần ai phối hợp.

Xong khi nào: hoàn thành checklist cuối bài tập 3.

## Phần 7 — Issue: kênh hỏi khi bị kẹt (10 phút)

Tự học thì issue là kênh hỏi chính của repo này:

1. Tab Issues, New issue, chọn template Question.
2. Kể rõ: đang làm bước nào, chạy lệnh gì, kết quả mong đợi là gì, thực tế ra sao. Paste đầy đủ error message.
3. Tiêu đề đi thẳng vào vấn đề: `[QUESTION] git push báo Permission denied dù đã accept invite`.

Cách hỏi tốt thì người trả lời đỡ mệt và bạn có câu trả lời nhanh hơn. Ba thói quen: paste full error thay vì chụp màn hình cropped, nêu command đã chạy, nêu những gì đã thử. Áp dụng luôn cho Slack.

Issue còn dùng để đề xuất. Xong lộ trình rồi thì mở một issue đề xuất cải thiện repo — thêm bài tập, đổi format, gì cũng được. Đây cũng là lần đầu bạn viết issue có tính xây dựng.

Trong PR description, thêm `Closes #5` (số issue tương ứng) thì issue tự đóng khi PR được merge.

Xong khi nào: đã mở ít nhất một issue, và biết dùng `Closes #X`.

## Checklist tốt nghiệp

Tự tick, đủ là xong:

- [ ] email git khớp GitHub (commit có avatar)
- [ ] clone repo thành công
- [ ] tạo branch riêng, commit, push
- [ ] mở PR đúng template, có reviewer
- [ ] review ít nhất một PR của bạn khác
- [ ] merge PR sau khi có approval, pull main về máy
- [ ] tự tạo conflict, gỡ, hiểu ba marker
- [ ] mở ít nhất một issue, biết dùng `Closes #X`

Đủ hết thì mở issue `[FEAT] Hoàn thành lộ trình self-study` kèm tên bạn. Thiện sẽ biết ai sẵn sàng sang phần nâng cao: GitHub CLI, Actions, CI/CD.

## Xử lý lỗi thường gặp

**`git push` báo Permission denied.** Hoặc bạn chưa accept invite vào org, hoặc git chưa có chứng thực. Cách nhanh nhất là dùng Personal Access Token: vào Settings, Developer settings, Personal access tokens, Tokens (classic), Generate new token, chọn scope `repo`. Lần push sau, git hỏi username thì nhập username, hỏi password thì dán token (không phải password GitHub).

Thích SSH thì vậy:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
cat ~/.ssh/id_ed25519.pub
# copy output, thêm vào Settings, SSH and GPG keys
ssh -T git@github.com   # hiện "Hi <username>!" là được
```

**`git commit` bảo nothing to commit.** Bạn chưa stage file. Chạy `git add .` trước.

**`git push` báo non-fast-forward.** Có ai đó vừa merge lên main trước bạn:

```bash
git pull --rebase origin main
git push
```

**Quên tên branch của mình.**

```bash
git branch -a
git checkout main
git pull
```

**Commit nhầm author.**

```bash
git commit --amend --author="Liem Bui <liem@asw.global>"
```

**Vim mở ra và không thoát được** (thường là sau `git commit`). Gõ `:wq` rồi Enter. Muốn đổi sang editor khác hẳn: `git config --global core.editor "code --wait"`.

## Đọc thêm

- [GitHub Docs — Pull requests](https://docs.github.com/en/pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [Pro Git](https://git-scm.com/book/en/v2) — đọc miễn phí, chương 2 và 3 là đủ dùng lâu
- [Learn Git Branching](https://learngitbranching.js.org/) — mô phỏng trực quan, chơi vài level là hiểu branch
- [Oh My Git!](https://ohmygit.org/) — game học git

---

Maintainer: Thiện (`thien-soy`). Review PR trong giờ làm việc, hỏi gấp thì Slack.
