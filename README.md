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

Lưu ý: quy tắc trên cho phép mọi người ghi dữ liệu, nên đừng chia sẻ link `#host` ra ngoài lớp.
