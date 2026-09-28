# Hệ Thống Quảng Bá Sản Phẩm WordPress - Môn TKQT HTPM
- Sinh viên: Dương Thị Hạnh
- MSV: DTC245230001
- Đề tài: Đề 3 - Website Quảng bá Sản phẩm (WordPress)

# 1. MÔ TẢ ĐỀ TÀI & KIẾN TRÚC HỆ THỐNG
Dự án thực hiện triển khai một hệ thống website quảng bá sản phẩm hoàn chỉnh dựa trên CMS WordPress, đảm bảo các tiêu chí về hiệu năng, an toàn thông tin, giám sát chỉ số (Metrics) và thu thập nhật ký (Logs) tập trung chuẩn Cloud-Native:
- Tầng Web & CSDL: WordPress kết nối MySQL 8.0, quản trị qua phpMyAdmin.
- Tầng Reverse Proxy: Nginx làm cổng giao tiếp duy nhất (Port 80), cấu hình Security Headers.
- Tầng Giám sát (Monitoring): Prometheus thu thập metrics tài nguyên container từ cAdvisor.
- Tầng Quản lý Log (Logging): Promtail thu thập log thời gian thực từ Docker socket và đẩy về Loki.
- Tầng Trực quan hóa (Visualization): Grafana tích hợp đồng thời Prometheus và Loki để vẽ biểu đồ và truy vấn LogQL.
- Biện pháp Hardening: Phân vùng mạng cách ly, phân quyền CSDL tối thiểu, ẩn cổng MySQL (3306) khỏi môi trường ngoài, mount volume cấu hình chế độ Read-Only.

# 2. TỔNG HỢP CÁC ĐỊA CHỈ TRUY CẬP HỆ THỐNG (IP: 192.168.36.129)
-  WordPress Site: http://192.168.36.129:80
-  phpMyAdmin Tool: http://192.168.36.129/pma/
-  Grafana Dashboard: http://192.168.36.129:3001 
-  Prometheus Metrics: http://192.168.36.129:9091
-  Loki API/Logs: http://192.168.36.129:3101
-  cAdvisor Monitoring: http://192.168.36.129:8080

# 3. Hướng dẫn khởi chạy
1. Yêu cầu: Đã cài đặt Docker và Docker Compose.
2. Lệnh khởi chạy toàn bộ hệ thống:
   docker compose up -d
3. Kiểm tra trạng thái các container
   docker compose ps
