# StudioLive

App máy tính (Electron) tạo cảnh tương tác cho TikTok LIVE, chạy hoàn toàn trên máy người dùng:

- **👻 Live Ma Online** — người xem hoá ma, gõ `hù` / `trốn` / `tìm` / `bùa` / `gọi hồn` / `tắt đèn`… để chơi với nhau; quà lớn gọi Bà Ma + jumpscare; vòng TRỐN TÌM định kỳ.
- **🪷 Đi Chùa Online** — chánh điện; người xem ngồi bồ đoàn, gõ `adidaphat` lên thắp hương; quà làm sen vàng nở, giọng đọc cảm ơn và chúc; thả tim đủ mục tiêu thì mưa hoa sen.

Mở tab nào thì cảnh đó chạy trên live. Thêm vào TikTok LIVE Studio bằng nguồn **Link** `http://lvh.me:3000` (1080×1920).

## Tài liệu

- [docs/HUONG-DAN-CAI-DAT.md](docs/HUONG-DAN-CAI-DAT.md) — cài đặt & sử dụng (gửi kèm cho người mua)
- [docs/BUILD.md](docs/BUILD.md) — đóng gói bản Mac / Windows (không ký số)
- [docs/THIRD_PARTY_NOTICES.md](docs/THIRD_PARTY_NOTICES.md) — giấy phép thư viện & tài nguyên

## Phát triển

```bash
npm install
npm start
```

## Cấu trúc

```
src/main.js       Tiến trình chính: cửa sổ, IPC, dữ liệu thử, tự kiểm tra (STUDIO_SELFTEST)
src/live.js       Quản lý kết nối TikTok, chuẩn hoá sự kiện, tự kết nối lại
src/direct.js     Đọc sự kiện qua trình duyệt ẩn + giải mã protobuf (tiktok-live-connector 2.0.0, MIT)
src/server.js     Server overlay Express + Socket.IO (chỉ 127.0.0.1) + giọng đọc /api/tts
src/tts.js        Giọng đọc tiếng Việt (Microsoft Edge, dự phòng Google)
src/settings.js   Lưu cài đặt trong thư mục userData
renderer/         Giao diện điều khiển
overlay/          Trang hiển thị trên live: game.js (Nhà Ma), temple.js (Đi Chùa), faces.js, audio.js
overlay/chua-assets/  Ảnh, nhân vật, hiệu ứng, nhạc của cảnh Đi Chùa
build/icon.png    Icon app
```

Cài đặt người dùng: `~/Library/Application Support/StudioLive/settings.json` (macOS), `%APPDATA%\StudioLive\settings.json` (Windows).
