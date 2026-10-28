# HiRes Music Studio — bản PWA đầu tiên

## Có gì trong bản này
- Trình phát tệp âm thanh cục bộ, danh sách phát, bài trước/tiếp, lặp bài, tua và âm lượng.
- Hỗ trợ những định dạng mà trình duyệt/thiết bị giải mã được: MP3, AAC/M4A, WAV, OGG/Opus và một số định dạng khác. **FLAC/AIFF không được hỗ trợ đồng đều trên mọi trình duyệt Android**.
- YouTube: tìm kiếm bằng cách mở kết quả tìm kiếm YouTube; có thể dán URL video để phát bằng trình phát nhúng chính thức.
- Audio Enhancer cục bộ dùng Web Audio API: EQ, compressor nhẹ, theo dõi mức tín hiệu.
- PWA có cache giao diện để mở lại offline sau lần tải đầu tiên qua HTTPS.

## Cách dùng trên Samsung A17
1. Giải nén ZIP.
2. Đưa toàn bộ tệp vào một repository GitHub (giữ nguyên cấu trúc).
3. Mở **Settings → Pages** của repository và chọn deploy từ nhánh `main` / thư mục root (hoặc dùng GitHub Actions để triển khai Pages).
4. Mở URL HTTPS của GitHub Pages trong Chrome hoặc Samsung Internet, chờ tải xong.
5. Chọn menu trình duyệt → **Thêm vào màn hình chính / Cài đặt ứng dụng**.
6. Chọn **Thêm nhạc từ thiết bị**, cấp quyền chọn tệp và phát. Tệp nhạc không được tải lên máy chủ.
7. Sau khi giao diện đã cache, phần giao diện có thể mở offline. Tệp nhạc phải được chọn lại nếu phiên trình duyệt bị đóng; bản MVP chưa lưu thư viện nhạc bền vững.

## Trên Windows
Mở qua HTTPS/localhost để PWA và service worker hoạt động đúng. Có thể chạy bằng VS Code Live Server hoặc một máy chủ web tĩnh.

## Giới hạn quan trọng, nói rõ để tránh hiểu nhầm
- Đây là bản web/PWA, không phải APK Android native.
- “Audio Enhancer” là DSP/EQ thực thời gian chạy trên thiết bị, **chưa phải AI thực sự** và không thể tái tạo chi tiết đã bị mất do nén. Nâng âm lượng/tăng treble không biến MP3 thành Hi-Res gốc.
- YouTube chạy trong iframe chính thức. Do giới hạn bảo mật/cross-origin và quy định dịch vụ, web app không thể lấy luồng âm thanh YouTube để đưa qua EQ của app, cũng không cung cấp tải nhạc/video YouTube.
- Tắt màn hình: phát nền tùy trình duyệt, Android và chính sách pin; PWA web không thể đảm bảo tiếp tục phát trên mọi máy. Nếu cần đảm bảo phát nền và xử lý mọi định dạng, bước tiếp theo nên là ứng dụng Android native.
- Chất lượng giải mã FLAC và các codec phụ thuộc hỗ trợ của trình duyệt; thử MP3/AAC/WAV trước nếu tệp không phát.
