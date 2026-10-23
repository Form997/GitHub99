# HAI ĐẤT GitHub Radar

Website tiếng Việt để khám phá kho GitHub theo lĩnh vực, giao diện CSS 3D, dịch mô tả, đồng hồ và thời tiết theo điểm chọn.

**Trang online:** https://hai-dat-github-radar.hai997.chatgpt.site

## Chạy trên máy

Cần Python 3 hoặc một máy chủ web tĩnh. Không cần npm, mô hình AI hay khóa API.

```sh
python -m http.server 8080
```

Mở http://localhost:8080. Định vị cần HTTPS hoặc localhost và quyền từ người dùng.

## Chức năng

- Tìm kiếm GitHub, lĩnh vực chia màu, sắp theo sao hoặc ngày cập nhật.
- Hiển thị tối đa 10 kho/giây từ bộ đệm; lấy dữ liệu theo lô 100 kho, mỗi 60 giây khi trang mở. Không thu thập khi đóng trang; tối đa 1.000 kết quả/truy vấn.
- Mục yêu thích và mục tiêu lưu trong trình duyệt.
- Dịch từng mô tả sang tiếng Việt bằng MyMemory; chọn ngôn ngữ gốc. Tên kho và mã nguồn giữ nguyên. Có giới hạn dịch vụ; bản dịch máy cần đối chiếu nguyên văn.
- Đồng hồ đổi theo múi giờ điểm chọn. Tìm địa danh hoặc xin quyền định vị để lấy thời tiết Open-Meteo; tọa độ làm tròn 0,01°, không lưu vị trí. Làm mới mỗi 15 phút khi trang mở. Đây là dữ liệu mô hình, không phải cảm biến tại chỗ.
- Mục “Mình đang làm gì?” giải thích truy vấn, mục tiêu và bước tiếp theo. Không phải đánh giá tự động chất lượng mã nguồn.

## Cấu trúc

| Tệp | Vai trò |
| --- | --- |
| index.html | Giao diện |
| style.css | Responsive và CSS 3D |
| app.js | GitHub, bộ đệm, yêu thích, lĩnh vực |
| features.js | Dịch, thời tiết, đồng hồ, hướng dẫn |
| seed.json | Dữ liệu khởi đầu, ghi nhận ngày 23/10/2026 |

## Cập nhật và triển khai

1. Sửa mã trên nhánh riêng, kiểm tra `node --check app.js` và `node --check features.js`.
2. Chạy máy chủ cục bộ; thử tìm kiếm, đổi lĩnh vực, lưu yêu thích, dịch, chọn địa danh và thay mục tiêu. Kiểm tra điện thoại và lỗi mạng/quyền vị trí.
3. Tăng hậu tố phiên bản CSS/JS trong index.html khi thay đổi nội dung để tránh cache cũ.
4. Commit và mở PR; sau kiểm tra, gộp nhánh rồi triển khai đúng phiên bản.
5. Trang Sites hiện dùng kho nguồn triển khai riêng. Đẩy GitHub KHÔNG tự cập nhật trang Sites; cần đồng bộ và triển khai bằng Sites. Không đưa .openai/hosting.json, token, mật khẩu hay thông tin người dùng vào bản xuất GitHub.

Chưa cấu hình lịch tự sửa mã hoặc tự đồng bộ GitHub–Sites. Khi yêu cầu cập nhật, cần lấy phiên bản mới nhất của cả hai nơi và xử lý khác biệt trước khi phát hành.

## Nguồn và giới hạn

- GitHub REST Search: https://docs.github.com/en/rest/search/search#search-repositories
- Open-Meteo: https://open-meteo.com/en/docs và https://open-meteo.com/en/docs/geocoding-api
- MyMemory: https://mymemory.translated.net/doc/spec.php

Các dịch vụ ngoài có hạn mức và điều khoản riêng. Số sao không bảo đảm chất lượng, an toàn hoặc quyền sử dụng. Đọc README và giấy phép của từng kho.

## Kiểm tra đã thực hiện

Ngày 23/10/2026: kiểm tra cú pháp JavaScript; tải 100 kho GitHub; lưu yêu thích; đổi bộ lọc lĩnh vực; dịch mô tả thực; tìm Huế và lấy dữ liệu thời tiết; đổi hướng dẫn theo mục tiêu nông nghiệp. Chưa kiểm tra định vị GPS trên điện thoại thật.
