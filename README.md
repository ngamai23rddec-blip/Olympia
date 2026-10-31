# OLYMPIA – THE PINK CHALLENGE

Website tĩnh (1 file `index.html`), đồng bộ thời gian thực bằng Firebase Realtime Database.

## 1. Tạo Firebase (miễn phí)
1. Vào https://console.firebase.google.com → Add project.
2. Build → **Realtime Database** → Create database (chọn vùng gần nhất, chế độ test).
3. Tab **Rules**, dán rồi Publish (dùng trong buổi thi, xong nên xóa project):
```
{ "rules": { ".read": true, ".write": true } }
```
4. Project settings → Your apps → Web (`</>`) → copy `firebaseConfig`.
5. Mở `index.html`, dán các giá trị vào `FIREBASE_CONFIG` (nhớ có `databaseURL`).

## 2. Đưa lên GitHub + Vercel
1. Tạo repo GitHub, upload `index.html` và `README.md`.
2. vercel.com → Add New → Project → chọn repo → Framework: **Other**, không cần build → Deploy.

## 3. Cách dùng
- MC: `https://ten-mien.vercel.app/#host` (soạn câu hỏi → Mở QR → BẮT ĐẦU).
- Máy chiếu: `.../#display`. Các đội quét QR trên màn chiếu.

## 4. Nhịp thời gian (mặc định, chỉnh ở Tổng quan → Thời gian)
- Câu hỏi hiện → chuông **sáng 10 giây** cho các đội vừa đọc đề vừa bấm. Hết 10s không ai bấm thì chuông tự đóng.
- Có đội bấm chuông → **3 giây** để trả lời. Hết 3s tự tính SAI (tắt được bằng ô “Hết giờ trả lời tự động tính SAI”).
- Đồng hồ dùng giờ máy chủ Firebase nên mọi điện thoại đếm khớp nhau. **Giữ tab MC (#host) luôn mở** – tab này chạy các mốc tự động.

## 5. Chung kết – Về đích
1. Mục **Câu hỏi** (khi đang chọn “Về đích”): soạn 4 người chơi × 4 gói (A–D) × 3 câu. Điểm mặc định A 10-10-10 · B 10-10-20 · C 20-20-10 · D 20-20-20, sửa được từng câu.
2. Mục **Điều khiển**: bấm “Mở bảng chọn gói cho Đội X” → màn chiếu và điện thoại đội đó hiện 4 gói; đội chạm chọn (MC cũng chọn thay được).
3. 3 câu hiện lần lượt; chuông đội đang chơi tắt, 3 đội còn lại bị khóa. Đội chơi sai/hết giờ → chuông 3 đội kia sáng (5s) để cướp quyền; hết người cướp thì hiện đáp án.
4. Điểm: đúng +điểm · sai −điểm · cướp đúng +điểm (đội sai ban đầu đã bị trừ lúc sai) · cướp sai −½ điểm.
5. **Ngôi sao hy vọng**: MC bấm trong mục Điều khiển, hiện trên màn chiếu và mọi điện thoại. Đội đang chơi đúng ×2, sai −×2.
6. Xong 3 câu bấm “Lượt tiếp theo” để sang đội kế.

Lưu ý: quy tắc trên cho phép mọi người ghi dữ liệu, nên đừng chia sẻ link `#host` ra ngoài lớp.
