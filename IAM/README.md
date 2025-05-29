# 🔐 IAM (Identity Access Management)

IAM là dịch vụ giúp bạn quản lý người dùng và quyền truy cập tài nguyên trên AWS một cách an toàn. Với IAM, bạn có thể:

- Tạo và quản lý người dùng (Users)
- Tạo và quản lý nhóm (Groups)
- Cấp quyền truy cập (Permissions)
- Tạo các chính sách (Policies) để kiểm soát chi tiết hành vi truy cập.

## 🧑‍💻 CÁC THÀNH PHẦN CHÍNH CỦA IAM

| Thành phần | Mô tả                                                                                                    |
| ---------- | -------------------------------------------------------------------------------------------------------- |
| **User**   | Tài khoản cá nhân, đại diện cho người hoặc ứng dụng.                                                     |
| **Group**  | Tập hợp các user dùng chung quyền. Gán policy cho group thì tất cả user trong group đều được quyền đó.   |
| **Role**   | Quyền tạm thời, thường dùng cho dịch vụ AWS hoặc user từ bên ngoài (SAML, Federation, EC2, Lambda...).   |
| **Policy** | Tài liệu định nghĩa quyền (cho phép hoặc từ chối hành động trên tài nguyên cụ thể), được viết bằng JSON. |

## 1. 👤 IAM User (Người dùng)

- Đại diện cho **con người hoặc ứng dụng**.
- Có thể đăng nhập vào AWS Console (dùng mật khẩu) hoặc qua CLI/SDK (dùng access key).
- Có thể gán **policy trực tiếp**.

**Ví dụ**:  
Tạo user `nguyen-dev`, gán quyền đọc ghi S3 → user có thể thao tác với S3 bucket.

## 2. 👥 IAM Group (Nhóm)

- **Tập hợp các user** có cùng quyền.
- Gán **policy vào group**, user trong group sẽ kế thừa quyền đó.
- Không thể đăng nhập, chỉ dùng để quản lý tập thể.

**Ví dụ**:  
Tạo group `Developers`, gán policy `AmazonS3FullAccess` → tất cả user trong group có quyền S3 đầy đủ.

## 3. 🎭 IAM Role (Vai trò)

- **Không phải user**, không có mật khẩu hay access key.
- Là bộ quyền tạm thời, dùng để **ủy quyền** cho:
  - Dịch vụ AWS (EC2, Lambda...)
  - Người dùng bên ngoài (qua SAML, federated login...)

**Ví dụ**:  
EC2 instance cần quyền đọc S3 → gán IAM role có quyền `s3:GetObject`.

### Use case

| Tình huống                          | Loại role                 |
| ----------------------------------- | ------------------------- |
| EC2 cần truy cập S3                 | Role for EC2              |
| Người dùng từ doanh nghiệp dùng AWS | Role with SAML/Federation |
| Lambda cần gọi DynamoDB             | Role for Lambda           |

## 4. 📜 IAM Policy (Chính sách)

- Tài liệu JSON mô tả **quyền truy cập**.
- Gắn cho **User**, **Group**, hoặc **Role**.
- Gồm các thông tin:
  - **Effect**: Cho phép (Allow) hoặc từ chối (Deny)
  - **Action**: Hành động (vd: `s3:PutObject`)
  - **Resource**: Tài nguyên cụ thể

1. Managed Policies

- Do AWS cung cấp hoặc do bạn tự tạo.
- Gắn trực tiếp vào User, Group, Role.

2. Inline Policies

- Chính sách riêng biệt chỉ gắn vào một thực thể cụ thể (user, group, role).
- Linh hoạt nhưng khó quản lý ở quy mô lớn.

**Ví dụ**:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": "s3:PutObject",
      "Resource": "arn:aws:s3:::my-bucket/*"
    }
  ]
}
```
