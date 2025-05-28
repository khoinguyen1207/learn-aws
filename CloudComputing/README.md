# Cloud computing

Cloud computing là mô hình cung cấp các dịch vụ điện toán — bao gồm servers, storage, databases, networking, software... thông qua Internet. Thay vì phải sở hữu và vận hành hệ thống vật lý, bạn có thể thuê tài nguyên từ các nhà cung cấp dịch vụ cloud như Amazon Web Services (AWS), Microsoft Azure, Google Cloud Platform (GCP).

| Mô hình           | Định nghĩa ngắn                                | Vị trí hạ tầng                     | Ưu điểm chính                                      | Nhược điểm chính                        | Ví dụ sử dụng                                   |
| ----------------- | ---------------------------------------------- | ---------------------------------- | -------------------------------------------------- | --------------------------------------- | ----------------------------------------------- |
| **On-Premise**    | Hạ tầng triển khai tại công ty                 | Tại chỗ (local data center)        | Toàn quyền kiểm soát, bảo mật cao                  | Chi phí cao, khó mở rộng                | Ngân hàng tự quản server                        |
| **Public Cloud**  | Dùng dịch vụ cloud từ bên thứ ba (AWS, GCP...) | Trên internet (nhà cung cấp)       | Dễ mở rộng, trả tiền theo nhu cầu                  | Dữ liệu trên cloud, ít kiểm soát vật lý | Startup host web trên AWS                       |
| **Private Cloud** | Cloud dành riêng cho 1 tổ chức                 | Có thể tại chỗ hoặc qua bên thứ ba | Bảo mật cao, tùy chỉnh linh hoạt                   | Chi phí xây dựng, bảo trì               | Doanh nghiệp lớn dùng OpenStack                 |
| **Hybrid Cloud**  | Kết hợp on-premise + public cloud              | Cả hai                             | Linh hoạt, cân bằng bảo mật và hiệu năng           | Quản lý phức tạp hơn                    | Chạy dữ liệu nhạy cảm local, còn lại trên cloud |
| **Multi-Cloud**   | Dùng nhiều nhà cung cấp cloud cùng lúc         | Trên nhiều nền tảng cloud          | Tránh phụ thuộc 1 nhà cung cấp, tận dụng điểm mạnh | Phức tạp trong quản lý và tích hợp      | Backend AWS, phân tích dữ liệu GCP              |

## Cloud Service Models

| Mô hình                         | Bạn quản lý                                   | Mô tả chi tiết                                                                                           | Ví dụ thực tế                                      |
| ------------------------------- | --------------------------------------------- | -------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| **Infrastructure as a Service** | Hệ điều hành (OS), runtime, ứng dụng, dữ liệu | Cung cấp cơ sở hạ tầng ảo hóa. Bạn có toàn quyền cài đặt OS, môi trường, và ứng dụng theo ý muốn.        | AWS EC2, Microsoft Azure VM, Google Compute Engine |
| **Platform as a Service**       | Mã nguồn ứng dụng và dữ liệu                  | Cung cấp nền tảng cho lập trình viên phát triển và triển khai ứng dụng mà không cần lo hạ tầng bên dưới. | Heroku, Google App Engine, Azure App Service       |
| **Software as a Service**       | Chỉ sử dụng ứng dụng                          | Người dùng truy cập ứng dụng qua trình duyệt. Không cần cài đặt, bảo trì hoặc cập nhật phần mềm.         | Gmail, Google Docs, Microsoft 365, Salesforce      |

📌 Tóm tắt nhanh:

- Infrastructure as a Service: Bạn tự lo cấu hình và triển khai (tự do cao).
- Platform as a Service: Bạn chỉ cần viết code, platform lo phần còn lại.
- Software as a Service: Bạn chỉ cần sử dụng, không cần biết gì về hạ tầng

# 🌍 AWS Global Infrastructure

## 1. Regions (Vùng)

- Là khu vực địa lý lớn chứa nhiều Availability Zones (AZs).
- Mỗi region là một vùng tách biệt vật lý.
- Ví dụ: `us-east-1`, `ap-southeast-1`, `eu-west-1`.

**Lưu ý**:

- Tài nguyên được tạo trong một region cụ thể.
- Dữ liệu không tự động sao chép giữa các region.

📌 Tại sao AWS phân chia thành nhiều region?

- **Đáp ứng pháp lý**: Một số tổ chức hoặc chính phủ yêu cầu dữ liệu không được rời khỏi quốc gia/khu vực.
- **Hiệu suất**: Người dùng tại Châu Á truy cập vào region Singapore sẽ nhanh hơn so với Ireland.
- **Khả năng phục hồi toàn cầu**: Dữ liệu và ứng dụng có thể sao lưu/phục hồi giữa các region trong trường hợp xảy ra sự cố lớn.

---

## 2. Availability Zones (AZs)

- Là một hoặc nhiều trung tâm dữ liệu riêng biệt trong một region.
- Có nguồn điện, mạng và làm mát độc lập.

**Lưu ý**:

- Mỗi region có ít nhất 2 AZs.
- Thiết kế đa AZ giúp tăng tính sẵn sàng và chống lỗi.

📌 Tại sao AWS phân chia thành nhiều AZ?

- **Tính sẵn sàng cao (High Availability)**: nếu một AZ bị sự cố (mất điện, cháy...), tài nguyên vẫn hoạt động từ AZ khác.
- **Chịu lỗi (Fault Tolerance)**: tránh sự cố lan rộng vì AZ được cô lập vật lý và mạng.
- **Khả năng mở rộng (Scalability)**: phân phối traffic, tài nguyên giúp scale hiệu quả.
- **Hỗ trợ dịch vụ AWS**: như RDS Multi-AZ, Load Balancer, Auto Scaling hoạt động hiệu quả hơn khi triển khai đa AZ.
- **Đáp ứng tiêu chuẩn doanh nghiệp**: giúp hệ thống đạt được yêu cầu về SLA, an toàn dữ liệu, disaster recovery.

---

## 3. Edge Locations

- Là điểm hiện diện (PoPs) để phân phối nội dung đến người dùng cuối.
- Dùng để cache nội dung hoặc tăng tốc độ truy cập từ người dùng cuối.
- Được sử dụng bởi:
  - Amazon CloudFront (CDN)
  - AWS Global Accelerator
  - Route 53 (DNS)

**Lưu ý**:

- Không nằm trong region, gần người dùng hơn.
- Giúp giảm độ trễ và tăng hiệu suất truy cập.

📌 Tại sao cần Edge Locations?

- **Giảm độ trễ (Latency)**: Đưa nội dung đến gần người dùng cuối hơn.
- **Tối ưu hiệu suất ứng dụng**: Đặc biệt với các ứng dụng media, video streaming, website tần suất truy cập cao.
- **Dịch vụ liên quan**:
  - **Amazon CloudFront** (CDN)
  - **Route 53** (DNS nhanh)
  - **Global Accelerator** (tăng hiệu suất routing)

---

## 4. Local Zones

- Là **mở rộng của một Region**, cung cấp tài nguyên gần hơn với người dùng cuối tại các khu đô thị lớn.
- Phục vụ ứng dụng yêu cầu **low-latency**.

**Ví dụ**: Local Zone ở Los Angeles.

📌 Tại sao cần Local Zones?

- **Độ trễ cực thấp**: Dành cho các ứng dụng như dựng phim, AR/VR, chơi game online thời gian thực, AI inferencing.
- **Gần user hơn cả AZs** của Region (có thể cách hàng trăm km).

---

## 5. Wavelength Zones

- Tối ưu cho ứng dụng sử dụng **5G**.
- Đặt trong cơ sở hạ tầng của nhà mạng.

**Mục đích**:

- Đáp ứng độ trễ cực thấp cho ứng dụng di động.

---

## 📊 Bảng So Sánh Tổng Quan

| Thành phần        | Vai trò chính                       | Đặc điểm nổi bật                         |
| ----------------- | ----------------------------------- | ---------------------------------------- |
| **Region**        | Khu vực độc lập địa lý              | Chứa nhiều AZs, cách xa nhau về địa lý   |
| **AZ (Zone)**     | Trung tâm dữ liệu độc lập           | Có mạng, điện, làm mát riêng             |
| **Edge Location** | Điểm gần user để phân phối nội dung | Dùng cho CloudFront, Route53             |
| **Local Zone**    | Mở rộng ngoài region chính          | Tăng tốc xử lý low-latency cho thành phố |
| **Wavelength**    | Tối ưu 5G + low-latency             | Tích hợp mạng di động                    |
