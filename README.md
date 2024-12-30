# Hệ Điều Hành Đơn Giản

## Tổng Quan Dự Án
Dự án này là một triển khai thực tiễn của **Hệ Điều Hành Đơn Giản**, được phát triển trong khuôn khổ môn học Hệ Điều Hành tại **Trường Đại Học Bách Khoa TP.HCM**. Dự án bao gồm các khái niệm chính của hệ điều hành, như thuật toán lập lịch, quản lý bộ nhớ và đồng bộ hóa tiến trình.

### Các Tính Năng Chính
- **Thuật Toán Lập Lịch**: Hệ thống lập lịch đa cấp hàng đợi (Multilevel Queue Scheduling - MLQ) với 140 mức độ ưu tiên giúp tối ưu hóa quản lý tiến trình.
- **Quản Lý Bộ Nhớ**: Triển khai ánh xạ địa chỉ dựa trên phân trang kết hợp phân đoạn để quản lý bộ nhớ hiệu quả.
- **Đồng Bộ Hóa**: Đảm bảo việc truy cập tài nguyên đồng thời an toàn, tránh các vấn đề như deadlock và race condition.

---

## Nội Dung Đã Thực Hiện
### Thiết Kế Bộ Lập Lịch
- **Multilevel Queue Scheduling (MLQ)**:
  - Phân chia tiến trình vào các hàng đợi ưu tiên khác nhau.
  - Phân bổ linh hoạt thời gian xử lý CPU cho từng hàng đợi.
  - Hỗ trợ xử lý đa bộ xử lý và đồng thời ở mức cao.
- **Các Hàm Đã Triển Khai**:
  - `enqueue()` và `dequeue()` để quản lý hàng đợi tiến trình.
  - `init_scheduler()` để khởi tạo các tham số của bộ lập lịch.
  - `get_mlq_proc()` để chọn tiến trình dựa trên mức ưu tiên.

### Quản Lý Bộ Nhớ
- **Ánh Xạ Bộ Nhớ Ảo**:
  - Hỗ trợ nhiều đoạn bộ nhớ (ví dụ: dữ liệu tĩnh và heap).
  - Chiến lược "heap go down" để tận dụng tối đa bộ nhớ khả dụng.
- **Ánh Xạ Địa Chỉ Dựa Trên Phân Trang**:
  - Kết hợp phân đoạn và phân trang để giảm phân mảnh bộ nhớ.
  - Tối ưu hóa việc cấp phát bộ nhớ cho các đoạn nhỏ và lớn.

### Đồng Bộ Hóa
- **Vấn Đề Đồng Bộ Hóa**:
  - Xung đột tài nguyên khi nhiều tiến trình truy cập cùng lúc.
  - Điều kiện tranh chấp và nguy cơ deadlock.
- **Giải Pháp**:
  - Sử dụng khóa (mutex) để đảm bảo an toàn khi truy cập tài nguyên chung.

---

## Kết Quả Kiểm Thử
### Lập Lịch
- Mô phỏng các tiến trình với mức ưu tiên và thời gian đến khác nhau.
- Quan sát quá trình lập lịch động dựa trên mức ưu tiên và lát cắt thời gian.

### Quản Lý Bộ Nhớ
1. **Ghi-Đọc Chồng Chéo**:
   - Kiểm tra tính chính xác dữ liệu khi thực hiện ghi đè trên cùng một vùng nhớ.
2. **Hiệu Quả Phân Trang**:
   - Thử nghiệm việc cấp phát vùng nhớ sử dụng các trang 256 byte.
3. **Cấp Phát Lại Động**:
   - Chứng minh khả năng tái sử dụng vùng nhớ đã được giải phóng.
4. **Phân Biệt malloc và alloc**:
   - Minh họa sự khác biệt giữa hai chiến lược cấp phát bộ nhớ.

---

## Hướng Dẫn Chạy Dự Án
### Yêu Cầu
- Trình biên dịch GCC
- Hệ thống tương thích POSIX

### Các Bước
1. Sao chép mã nguồn:
   ```bash
   git clone <repository-url>
   cd SimpleOperatingSystem
   ```
2. Biên dịch mã nguồn:
   ```bash
   make all
   ```
3. Chạy chương trình mô phỏng:
   ```bash
   ./scheduler input_file
   ```

---

## Kết Quả Học Tập
Dự án giúp hiểu sâu hơn về:
- Triển khai thực tế các thuật toán lập lịch và quản lý bộ nhớ.
- Tương tác giữa phần cứng và phần mềm trong hệ điều hành.
- Gỡ lỗi và tối ưu hóa mã hệ thống.

