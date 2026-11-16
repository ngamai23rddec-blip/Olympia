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


## V12.1 – Sửa tính điểm Về đích & thêm vòng chơi thử
- **Về đích – chơi gói:** không dùng ngôi sao: đúng +điểm câu, sai giữ nguyên điểm (không trừ). Dùng ngôi sao hy vọng: đúng ×2 điểm câu, sai −đúng số điểm câu.
- **Về đích – cướp quyền:** đúng +½ điểm câu, sai −½ điểm câu (không nhân đôi theo ngôi sao).
- **Vòng chơi thử (xé nháp):** chọn ở Tổng quan › Thiết lập › "Vòng chơi thử". Chơi như Vòng loại (bấm chuông, cướp quyền); tự thêm 3 câu mẫu lần đầu (sửa/xóa/thêm ở mục Câu hỏi). Điểm lưu riêng, không tính vào Vòng loại/Chung kết; có nút "Xóa điểm vòng thử".

## V12.2 – Vòng quay & Điều khiển cuộc thi
- Vòng quay: khi quay xong, tên nhóm trúng phóng to toàn khung ("NHÓM n" + Lượt 1/2) cùng nhạc fanfare (trống dồn → kèn → chuông lấp lánh) và pháo giấy. Tự đóng sau ~5,5s hoặc bấm để đóng.
- Mục "Điều khiển cuộc thi": thu nhỏ nút, chữ và khoảng cách để thấy toàn bộ bảng điều khiển trong một màn hình.

## V12.3
- Sửa bố cục nút ở Điều khiển cuộc thi: nút không còn bị tràn/xuống dòng, các khối tự xếp hàng cân đối.


## V13
**1. Hiện đáp án rồi chờ MC**
- Mọi vòng thi: sau khi trả lời xong, đáp án hiện trên Display và **giữ nguyên** cho đến khi MC bấm *Câu tiếp theo*.
- Đã bỏ bảng xếp hạng tự hiện sau mỗi câu. Bảng điểm ở đáy màn hình vẫn còn và được làm lại: avatar tròn + huy hiệu hạng, tên, ô điểm, màu nhấn theo đội, viền vàng cho hạng 1.
- Đáp án tự hiện khi: trả lời đúng; trả lời sai mà câu không cho cướp quyền (Multiple Choice / True or False); mọi đội đã mất quyền; hết giờ cướp quyền mà không ai bấm. Nếu câu cho cướp quyền và không bật tự động mở chuông, MC tự bấm *Mở lại chuông* hoặc *Hiện đáp án*.
- Nút "Chiếu bảng xếp hạng lên màn chiếu" (thủ công) vẫn giữ.

**2. Tự động mở chuông cướp quyền** — Tổng quan › Thiết lập › tick "🔔 Tự động mở chuông cướp quyền sau khi trả lời sai" (mặc định tắt). Chuông cướp quyền mở lại ngay sau khi một đội trả lời sai (chỉ với câu cho phép cướp quyền).

**3. Chat ở thanh trái** — khung chat nằm dưới mục Tổng quan, chỉ hiện khi đã mở phòng (Mở QR / đang thi), có thể thu gọn. Giữ các nút cũ (Bật/Tắt chat, QR chat, Sao chép link, Xoá tin nhắn, Bật/Tắt vote, Reset vote, Mở lại người bị loại) và hiện luôn khung bình luận trực tiếp. Mỗi bình luận có nút **Cảnh cáo** (hiện robot cảnh báo trên Display và thông báo trên điện thoại người đó; cảnh cáo lần 2 = bị loại) và **Kick** (loại khỏi chat ngay).

**4. Loại câu hỏi mới** "Câu hỏi – xem xong mới hiện video": Display hiện câu hỏi trước, MC bấm *Phát video* trong Điều khiển cuộc thi; video xong thì chuông mở. Loại "Video – xem xong mới hiện câu hỏi" giữ nguyên cách chạy. Cả hai loại cần Link video. Đồng hồ/chuông bắt đầu **sau khi video kết thúc**; video không còn bị phát lại khi mở lại chuông.

**5. Nhạc Lobby: 5 bài** — thêm 3 bài (âm lượng đã cân bằng), có danh sách chọn bài, tên bài + số thứ tự cập nhật ngay khi chuyển bài (trên MC và trên Display Lobby), hết bài tự chuyển bài kế tiếp.


## V14
1. **Vòng quay chuyển sang màn hình Display:** nút vòng quay nhỏ ở trên cùng giữa màn hình; bấm vào sẽ mở rộng ra **toàn màn hình** (hiệu ứng vòng tròn loe ra từ nút). Bấm vào vòng quay để quay, hiện kết quả nhóm + lượt ở hai bên. Đóng bằng nút × hoặc phím Esc. Bên MC chỉ còn bảng kết quả Lượt 1/Lượt 2, nút Đặt lại và Sơ đồ đấu.
2. **Nhạc nền:** bấm *BẮT ĐẦU* nhạc vẫn tiếp tục phát; chỉ tắt khi MC bấm *Bắt đầu câu 1*.
3. **Multiple Choice được cướp quyền** (kể cả các câu MC đã soạn từ trước). Chỉ còn True or False không cho cướp quyền.
4. Vòng quay tự ẩn khi MC bấm BẮT ĐẦU (vào phần thi).
