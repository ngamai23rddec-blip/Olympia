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
