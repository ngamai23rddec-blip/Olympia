# OLYMPIA – THE PINK CHALLENGE · V9

## Nâng cấp trong V9
1. **Màn hình trao giải:** mỗi bục hiển thị mascot mà đội đã chọn, bên cạnh tên đội và điểm số.
2. **Mã QR:** thu gọn kích thước trong cửa sổ nổi, giới hạn chiều cao theo màn hình, giữ QR cân đối và không bị cắt ở màn hình laptop.
3. **Câu hỏi video:** trong form thêm câu hỏi có trường Link video. Hỗ trợ MP4/WebM/Ogg (tự mở câu hỏi khi video kết thúc), YouTube (dùng YouTube IFrame API để nhận sự kiện kết thúc) và URL nhúng iframe; có nút xác nhận dự phòng.
4. **Danh sách câu hỏi:** bố cục compact dạng hai tầng, nội dung không còn bị ép thành cột chữ hẹp; các ô thời gian và nút thao tác nhỏ hơn.
5. **Phòng chờ Display:** lobby mới hiển thị mã phòng, QR, bốn vị trí đội và mascot đã chọn. Mascot có chuyển động nhún; bong bóng hội thoại thay đổi định kỳ với lời thoại vui vẻ/cà khịa nhẹ.

## Cách chạy
- Giải nén toàn bộ ZIP.
- Giữ `index.html` và thư mục `assets/` cùng cấp.
- Deploy lên hosting HTTPS như GitHub Pages, Netlify hoặc Vercel.
- Cấu hình Firebase như bản trước.

## Lưu ý video
- Nên dùng đường dẫn video MP4 trực tiếp hoặc URL YouTube công khai.
- Với video MP4, câu hỏi tự hiện sau sự kiện `ended`.
- Với YouTube, cần kết nối internet để tải YouTube IFrame API; nút “Video đã kết thúc · Hiện câu hỏi” là phương án dự phòng.
- Nếu URL iframe của nền tảng khác không phát sự kiện kết thúc, MC/Display có thể dùng nút xác nhận dự phòng.
- Video được phát trên màn hình Display; các điện thoại đội sẽ ở trạng thái chờ cho đến khi video hoàn tất.

## Kiểm tra
- JavaScript inline đã được kiểm tra cú pháp bằng Node.js.
- Chưa thực hiện kiểm thử end-to-end với Firebase hoặc nhiều thiết bị thật.


## V10 — Live Mascot Lobby

### Cách mở phòng chờ
1. Mở trang MC và kết nối Firebase như bình thường.
2. Trong Dashboard, vào **Tổng quan** và nhấn **Mở QR** để đặt trạng thái phòng thành `lobby`.
3. Mở màn hình **Display** (nút Mở Display hoặc mở `#display` ở tab riêng).
4. Khi các đội quét QR và chọn mascot, các thẻ mascot sẽ xuất hiện trên Display.
5. Khi MC nhấn **BẮT ĐẦU**, Display chuyển sang màn hình thi đấu.

### Nâng cấp V10
- Lobby có khu vực hội thoại trung tâm, hiển thị rõ nhân vật đang nói và đội đang được đáp lời.
- Các mascot luân phiên mở lời và đáp trả theo cá tính riêng; có câu cà khịa, cổ vũ, ngơ ngác, mít ướt và phản ứng hài hước.
- Mascot đang nói sẽ nhún/bật lên; nhân vật được đáp lời có chuyển động phản ứng.
- Bong bóng trên từng thẻ đội cập nhật theo lượt hội thoại.
- Khi chưa có đội hoặc mới có một đội, Lobby hiển thị lời chào/độc thoại thay vì để màn hình trống.
- Giữ nguyên Firebase, luật chơi, các màn hình thi đấu, câu hỏi video và bộ 10 mascot.

### Lưu ý
Lobby chỉ hiển thị khi trạng thái phòng là `lobby`. Nếu Display đang hiện “Chuẩn bị…” hoặc giao diện câu hỏi thì phòng đã ở trạng thái khác; quay lại MC và nhấn **Mở QR** trước khi bắt đầu thi. Để hội thoại qua lại giữa nhiều mascot, cần ít nhất hai đội đã tham gia.


## V10.3 – Nhạc nền & QR
- Thêm nhạc nền chiptune vui nhẹ, có nút bật/tắt riêng; cần thao tác bấm lần đầu do giới hạn autoplay của trình duyệt.
- Gỡ nút Mã QR khỏi thanh tiêu đề dashboard.
- Gỡ QR nhúng ở phòng & QR và màn hình Lobby; mã QR chỉ xuất hiện trong hộp thoại khi MC bấm bước “Mở mã QR cho các đội vào”.


## V10.4 — Love Story Lobby Music Player
- Extracted audio-only MP3 tracks from the two user-uploaded videos; no video is shown in the player.
- Both full clips are included as separate tracks in `assets/music/`.
- Host dashboard right rail controls Display playback: previous/next, play/pause and volume.
- Music is intended for Lobby only and pauses when Display leaves Lobby.
- Browser autoplay policy may require one click on the Display's “Bật âm thanh Display” prompt the first time.

## V10.5 – Awards stage, answer reveal status, and music seeking
- Redesigned the Display awards screen with a more polished grand-finale stage, layered lighting, richer podium/cards, and stronger reveal animations.
- The Host answer panel turns green after the answer is revealed on Display.
- Added a draggable Lobby music seek bar with elapsed/total time.
- Fixed track switching by tracking the selected audio source explicitly; changing tracks now resets playback to the beginning and updates the track title immediately.
- Volume changes no longer reset the playback position.


## V10.7 – Draw wheel and tournament bracket
- Replaced the Host sidebar Quick Access panel with a compact, colorful draw wheel.
- The draw follows the configured fixed sequence: 3, 5, 8, 2, 1, 9, 6, 7.
- Results are assigned alternately to Lượt 1 and Lượt 2, removed from the remaining wheel, and saved in Firebase room state.
- Once all eight groups are drawn, the bracket view shows four Vòng loại pairings and the advancement path into Chung kết.
- Added reset and bracket-preview controls.


## V10.8 – Enlarged draw wheel and two-round qualification
- Clicking the compact wheel opens a large wheel modal on the Host.
- The pointer is fixed at the top; the wheel's final rotation is calculated so the selected group sector lands exactly under the pointer, matching the predetermined draw order.
- Added spinning tick sounds and a result chime using Web Audio.
- Reworked the bracket: Vòng loại has two rounds of four groups each; the top two scorers from each round qualify for a four-team Chung kết.

## V11 — Chat bình luận, vòng quay mới, sơ đồ mới

**Chat bình luận**
- Link trang chat: `index.html#chat-MÃPHÒNG` (MC bấm *QR chat* hoặc *Sao chép link* ở bảng "Chat bình luận" bên phải màn hình MC; hoặc vào trang chủ bấm *Vào chat* rồi nhập mã phòng).
- Người xem tự đặt biệt danh, gửi bình luận → hiện ngay ở khung chat bên phải màn hình Display (realtime qua Firebase Realtime Database, nhánh `chat/<mã phòng>`).
- Tự chặn tin nhắn có dấu hiệu lộ đáp án khi câu hỏi đang hiển thị (A/B/C/D, "chọn B", "đáp án là C", Ây/Bờ/Cờ/Dờ/Bê/Cê/Dê, bee/see/dee…). Robot nhắc nhở trên Display.
- Spam (nhắn dồn dập, lặp nội dung, kéo dài ký tự, gắn link) hoặc ngôn từ không phù hợp: lần 1 robot cảnh báo "CẢNH BÁO: [NICKNAME] SỬ DỤNG NGÔN TỪ CHƯA PHÙ HỢP!!!!!", lần 2 bị loại khỏi khung chat (MC có thể "Mở lại").
- MC có thể Bật/Tắt chat, Xoá tin nhắn.
- Firebase Realtime Database rules cần cho phép đọc/ghi nhánh `chat` giống các nhánh hiện có (ví dụ `".read": true, ".write": true`).

## V12 — Vote thả tim
- Trên trang chat (điện thoại): hàng 4 nút tim, mỗi người bình chọn 1 đội mong muốn thắng; bấm đội khác để đổi, bấm lại để bỏ tim.
- Display: bảng xếp hạng bình chọn nằm dưới khung bình luận (đã thu nhỏ), cập nhật realtime, có tim bay khi có phiếu mới.
- MC: nút Bật/Tắt vote và Reset vote trong bảng "Chat bình luận". Phiếu của người bị loại khỏi chat không được tính.
- Dữ liệu lưu ở `chat/<mã phòng>/votes/<uid>` (cùng nhánh `chat`, không cần đổi rules).
