# ⚙️ Amazon EC2 (Elastic Compute Cloud)

## 1. 💡 EC2

- EC2 (Elastic Compute Cloud) là dịch vụ **máy chủ ảo (virtual server)** có thể cấu hình, chạy trên nền tảng đám mây AWS.
- Cho phép bạn **thuê máy tính theo giờ/giây** để chạy ứng dụng giống như trên máy chủ vật lý.

---

## 2. 🔧 Thành phần chính của EC2

### ✅ AMI (Amazon Machine Image)

- Là bản sao của hệ điều hành + phần mềm bạn cần.
- Dùng để tạo nhiều instance giống nhau.

### ✅ Instance Type

- Xác định cấu hình phần cứng của EC2 (CPU, RAM, mạng, ổ đĩa).
- Phân loại theo nhóm:
  - **t** – General Purpose (t3, t4g...)
  - **m** – General Purpose (m6g, m5...)
  - **c** – Compute Optimized
  - **r** – Memory Optimized
  - **g/p/inf** – Accelerated Computing (GPU, inference...)

### ✅ Instance

- Là một máy chủ ảo đang chạy.
- Bạn có thể start, stop, terminate nó.

### ✅ Key Pair

- Cặp khóa (public/private) dùng để SSH vào EC2.
- AWS lưu khóa public, bạn giữ private.

### ✅ Security Group

- Firewall ảo điều khiển traffic vào/ra EC2 instance.
- Mở cổng như 22 (SSH), 80 (HTTP), 443 (HTTPS)...

---

## 3. 💰 Các mô hình giá EC2

| Mô hình          | Mô tả nhanh                                                        |
| ---------------- | ------------------------------------------------------------------ |
| **On-Demand**    | Trả phí theo giờ hoặc giây, không cam kết. Linh hoạt, giá cao.     |
| **Reserved**     | Cam kết sử dụng 1 hoặc 3 năm. Giá rẻ hơn nhiều.                    |
| **Spot**         | Mua công suất thừa, rẻ hơn 90%, nhưng có thể bị thu hồi.           |
| **Savings Plan** | Giảm giá dựa trên cam kết sử dụng compute, linh hoạt hơn reserved. |

---

## 4. 🚀 Các tính năng nổi bật

### ☁️ Auto Scaling

- Tự động tăng/giảm số lượng EC2 dựa trên tải hệ thống.

### ⚖️ Load Balancer (ELB)

- Phân phối traffic đến nhiều EC2 để tăng tính sẵn sàng.

### 📂 EBS (Elastic Block Store)

- Ổ đĩa lưu trữ lâu dài cho EC2.
- Có thể tách rời, backup, resize.

### 🧱 Placement Groups

- Tối ưu vị trí đặt instance (clustered/spread/partitioned) → tối ưu hiệu năng hoặc chịu lỗi.

---

## 5. 🛡️ Bảo mật và kết nối

- **Security Groups**: Firewall kiểm soát inbound/outbound traffic.
- **Key Pair**: Xác thực đăng nhập SSH.
- **IAM Roles**: Cấp quyền truy cập AWS services từ EC2.
- **Elastic IP**: Địa chỉ IP tĩnh gán vào EC2 để public access.

---

## 6. 🧪 Các trường hợp sử dụng EC2

| Use Case                 | Mô tả ngắn                              |
| ------------------------ | --------------------------------------- |
| Web/App hosting          | Triển khai website, app backend         |
| Batch processing         | Chạy các tác vụ xử lý dữ liệu định kỳ   |
| High performance compute | Machine learning, big data, simulation  |
| Development & test       | Môi trường dev/test ngắn hạn, linh hoạt |
| Gaming servers           | Chạy game servers thời gian thực        |

---

## 7. 🧠 Note

- EC2 = "máy chủ ảo thuê theo nhu cầu".
- **AMI** = Hệ điều hành + phần mềm sẵn sàng chạy.
- **Instance Type** = Phần cứng ảo hóa (CPU/RAM/v.v).
- **Security Group** = Tường lửa kiểm soát cổng.
- **Key Pair** = Cách đăng nhập bảo mật qua SSH.
- **Auto Scaling** + **ELB** = Tạo hệ thống linh hoạt và chịu tải cao.

---

📚 **Tài liệu AWS chính thức**: https://docs.aws.amazon.com/ec2/index.html  
📚 **Repo github **: https://github.com/hoanglinhdigital/aws-cloud-for-beginner/tree/master/computing-service-ec2
