# Triển khai Ngoại Khoa Quest lên Vercel

## Cách 1 — Vercel CLI (không cần GitHub)

1. Cài Node.js LTS (https://nodejs.org/).
2. Giải nén gói ZIP vào thư mục bất kỳ.
3. Mở PowerShell/Terminal **tại thư mục chứa `index.html` và `vercel.json`**.
4. Chạy:

   ```bash
   npx vercel login
   npx vercel --prod
   ```

5. Khi được hỏi, tạo project mới và dùng cấu hình phát hiện từ `vercel.json`. Nếu cần chọn Framework Preset, chọn **Other**; Output Directory **`.`**; không cần Build Command.
6. CLI sẽ in ra URL có dạng `https://ten-du-an.vercel.app`. Truy cập URL này để mở app.

Lần sau, cập nhật file trong cùng thư mục rồi chạy `npx vercel --prod`.

## Cách 2 — GitHub + Vercel (tự triển khai khi cập nhật)

1. Tạo một repository GitHub mới.
2. Upload **nội dung bên trong thư mục ZIP**, để `index.html` và `vercel.json` nằm ở **thư mục gốc repository** (không bọc thêm một cấp thư mục).
3. Truy cập https://vercel.com/new -> **Import Git Repository** -> chọn repository.
4. Framework Preset **Other**, Build Command **để trống**, Output Directory **`.`** -> Deploy.
5. Mỗi lần push lên nhánh production, Vercel triển khai lại tự động.

## Kiểm tra PWA

- Truy cập `https://TEN-DU-AN.vercel.app/`.
- Kiểm tra `https://TEN-DU-AN.vercel.app/manifest.webmanifest`, `/sw.js`, `/questions.json` không trả 404.
- Android: Chrome -> menu -> Install app / Add to Home screen.
- iOS: Safari -> Chia sẻ -> Thêm vào Màn hình chính.
- Mở ứng dụng ít nhất một lần khi có mạng, sau đó thử ngắt mạng và mở lại.
- Khi cập nhật bộ câu hỏi hoặc mã nguồn, tăng phiên bản cache trong `sw.js` (ví dụ `v2` -> `v3`) để app tải phiên bản mới.

## Lưu ý

- Dữ liệu học và câu sai hiện lưu bằng `localStorage` trên từng trình duyệt/thiết bị; không đồng bộ khi đổi máy.
- Ứng dụng chưa có đăng nhập, backend hay bảng xếp hạng chung.
- Vercel không mặc nhiên biến app thành ứng dụng App Store/Google Play.
- Tài liệu đi kèm gồm 27 trang chụp và ngân hàng 402 câu; 7 câu được đối chiếu ảnh gốc, 395 câu nhập từ HTML nguồn và 59 câu kèm ghi chú.
