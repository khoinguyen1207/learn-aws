# File note

### 1. Tạo key pair trong AWS EC2

`er2-key-pair.pem`: Dùng lúc tạo instance EC2 và dùng để connect tới instance đó.

- Lưu ý: Dùng lệnh `chmod 400 er2-key-pair.pem` để set quyền truy cập cho file trước khi sử dụng.

### 2. Tạo IAM user

`developer_credential.csv`: Thông tin đăng nhập IAM user sau khi tạo user.

### 3. Tạo IAM access key

`developer_accessKeys.csv`: Access key của IAM user, có thể set vào `aws configure` để sử dụng AWS CLI.

### 4. Add member vào instance EC2

`dev01.pub` và `dev01`: Đây là cặp khóa SSH dùng để kết nối tới instance EC2.

- Lưu ý: File `dev01.pub` là public key, còn file `dev01` là private key.
