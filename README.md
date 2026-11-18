# Ngoại Khoa Quest — PWA ôn tập bệnh ngoại khoa

Ứng dụng tĩnh HTML/CSS/JavaScript, không cần backend, không cần `npm install`, có thể triển khai trên GitHub Pages, Netlify, Cloudflare Pages hoặc một máy chủ HTTPS bất kỳ.

## Khởi chạy trên máy tính

Tại thư mục chứa `index.html`:

```bash
python -m http.server 8080
```

Mở `http://localhost:8080` trong trình duyệt.

## Triển khai để cài trên iOS / Android

1. Tải **toàn bộ nội dung thư mục** lên một website HTTPS, ví dụ GitHub Pages hoặc Netlify.
2. Mở URL bằng Safari (iPhone/iPad) → Chia sẻ → Thêm vào Màn hình chính.
3. Mở URL bằng Chrome (Android) → menu → Cài đặt ứng dụng.
4. Sau lần tải đầu tiên và khi service worker đã lưu cache xong, ứng dụng có thể chạy ngoại tuyến. Trên điện thoại cần truy cập HTTPS, `file://` không hỗ trợ PWA.

## Chức năng

- Học 5 câu, toàn bộ ngân hàng, theo chủ đề, ôn riêng câu đã trả lời sai.
- Phản hồi ngay, đáp án và giải thích, liên kết tới ảnh tài liệu gốc.
- XP, combo trả lời đúng liên tiếp, streak ngày học, danh hiệu, thống kê, lịch sử.
- Lưu tiến độ cục bộ bằng localStorage, xuất/khôi phục bản sao lưu.
- Nhập thêm ngân hàng JSON từ giao diện (mẫu có thể tải trong Cài đặt).
- 27 ảnh chụp gốc, đã xoay ảnh và tối ưu thành WebP, tích hợp xem ảnh.
- PWA: manifest, service worker cache tài liệu, icon màn hình chính.

## Lưu ý về nội dung

ZIP đính kèm chứa 27 ảnh chụp tài liệu. Do nhiều trang bị mờ, nghiêng, ảnh chụp hai trang trên một khung và đáp án OCR dễ sai, **bản này chỉ tích hợp 7 câu đầu của ảnh số 1 được đọc và đối chiếu trực quan với đáp án in sẵn**. Tất cả 27 ảnh được giữ ở Thư viện để đối chiếu và bổ sung sau. Không tự động gán đáp án cho các câu OCR chưa kiểm định.

Kiến thức được sao chép theo ngân hàng ôn tập và **không phải hướng dẫn chẩn đoán hoặc điều trị**.

## Định dạng câu hỏi JSON

```json
[
  {
    "id": "them-001",
    "topic": "Chủ đề",
    "question": "Nội dung câu hỏi?",
    "options": ["A", "B", "C", "D"],
    "answer": 0,
    "explanation": "Giải thích (tùy chọn)"
  }
]
```

`answer`: 0 = A, 1 = B, 2 = C, 3 = D. ID phải duy nhất.

## Quyền riêng tư

Không có tài khoản, không có API hoặc máy chủ ghi dữ liệu cá nhân. Dữ liệu học trên thiết bị, phải xuất sao lưu nếu muốn chuyển máy. Google Fonts (nếu tải được) là tài nguyên phụ trợ, ứng dụng có font dự phòng khi ngoại tuyến.

## Host trên Vercel

Xem hướng dẫn `DEPLOY-VERCEL.md`. Thư mục này đã có `vercel.json` và sẵn sàng deploy dưới dạng static site.
