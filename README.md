# Bách Nghệ hình tụ · Photobooth

Web photobooth tiếng Việt cho triển lãm làng nghề. Vite + Canvas, không cần backend hoặc API key.

## Phát triển

Node.js 24, `npm ci`, sau đó `npm run dev`. `npm run build` tạo `dist`; `npm run preview` chạy bản build.

Luồng: vẽ icon dynamic trong 60 giây (tính từ nét đầu tiên) → chọn khung 1/2/3 ảnh → cho phép camera, đếm ngược 3 giây mỗi ảnh → xem bộ ảnh, tải PNG hoặc chia sẻ tệp nếu trình duyệt hỗ trợ. Có hoàn tác, tẩy, điều chỉnh nét và ba bộ lọc. Ảnh và nét vẽ chỉ nằm trong bộ nhớ trình duyệt. Tải lại trang sẽ xóa phiên.

Camera yêu cầu HTTPS hoặc localhost và quyền camera từ trình duyệt. Chế độ ảnh mẫu có nhãn rõ ràng để thử trên máy không có camera. Chưa có in ảnh, QR tải qua điện thoại hay lưu đám mây: các tính năng đó cần tích hợp riêng. Bảng màu được đối chiếu từ ảnh tham chiếu; logo chữ lấy từ SVG người dùng cung cấp. Font Be Vietnam Pro được đóng gói cục bộ.

## Kiểm thử

`npx playwright test` chạy kiểm thử hành trình với ảnh mẫu, xuất PNG, responsive và giới hạn thời gian. Cấu hình hiện dùng Chromium tại `/usr/bin/chromium`; chỉnh executablePath nếu máy dùng đường dẫn khác. Có thể kiểm thử camera vật lý trên thiết bị sự kiện qua HTTPS.

## GitHub Pages

Workflow `.github/workflows/pages.yml` build và deploy khi push `main`. Trong Settings → Pages, chọn Source: GitHub Actions nếu repository chưa bật Pages. Địa chỉ dự kiến sau khi deploy thành công: https://vuminhdesign10-top.github.io/bnkk_photobooth/ . Không cần đưa ảnh người dùng lên GitHub.

## Giao diện máy photobooth

Màn hình chờ có nút Chạm để bắt đầu. Các màn hình thao tác rút gọn nội dung, nút cảm ứng lớn và nút Toàn màn hình (cần người dùng chạm). Bố cục đã được kiểm thử tại 1366×768, 1920×1080 và 1080×1920. Sau khi tải ảnh, chọn Xong · Lượt tiếp theo để xóa phiên và trở về màn hình chờ. Chia sẻ/tải xuống phụ thuộc trình duyệt của máy; chưa tích hợp máy in hay QR chuyển ảnh sang điện thoại.
