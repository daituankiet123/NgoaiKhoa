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
- Ngân hàng 402 câu: 7 câu đã đối chiếu với ảnh gốc và 395 câu trích từ tệp HTML 400 câu (bỏ 5 câu trùng). Có 59 câu kèm ghi chú của tài liệu nguồn; các ghi chú được hiển thị khi trả lời.
- PWA: manifest, service worker cache tài liệu, icon màn hình chính.

## Lưu ý về nội dung

Tệp `questions.json` giữ 7 câu đã đối chiếu trực quan với ảnh gốc và bổ sung 395 câu từ tệp HTML `tracNghiemNgoaiKhoa.html`. Các câu HTML có đáp án theo tài liệu nguồn, chưa được xác minh độc lập với ảnh. 59 câu có ghi chú/cảnh báo từ nguồn được giữ lại trong phần giải thích khi làm bài. Năm câu trùng nội dung đã được lược bỏ để tránh lặp. Các ảnh gốc tiếp tục có trong Thư viện để đối chiếu.

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

## Hiệu ứng khi làm bài

- Câu đúng có hiệu ứng sáng nhẹ và hạt màu; câu sai có rung nhẹ để làm nổi phần phản hồi.
- Bài đúng tất cả câu hiện meme 10 điểm. Nếu số câu sai lớn hơn một nửa tổng số câu, hiện meme động viên.
- Tôn trọng cài đặt giảm chuyển động của thiết bị.
