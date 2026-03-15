# <img width="50" alt="login" src="https://github.com/user-attachments/assets/79247a8a-20a7-4eaa-8029-8cd01302ecc6" /> Ứng dụng bán đồ ăn trực tuyến
## Nguyễn Đăng Tú - 0109367

Đây là ứng dụng đồ ăn được phát triển sử dụng kiến thức từ môn học **Lập trình đa nền tảng**. Ứng dụng cho phép người dùng đặt mua đồ ăn, quản lý đơn hàng và thông tin cá nhân một cách thuận tiện trên thiết bị di động.

## 1.🚀 Tổng quan

### 🛍️ Tính năng chính (Dành cho người dùng)
- Quản lý tài khoản người dùng
  - Đăng nhập: Sử dụng JWT để xác thực người dùng.
  - Cập nhật thông tin cá nhân: Họ tên, số điện thoại, địa chỉ,...
- Xem danh sách đồ ăn 
  - Xem theo danh mục(tên loại đồ ăn)
  - Tìm kiếm theo tên.
  - Chi tiết sản phẩm: tên đồ ăn, thông tin mô tả, giá tiền, ảnh minh họa.
- Thêm vào giỏ hàng, đặt hàng
  - Xem giỏ hàng
  - Cập nhật số lượng đồ ăn (thêm, giảm, xóa) giỏ hàng.
  - Đặt hàng: đơn sẽ được lưu vào lịch sử đơn chờ ghi nhận và xủ lý.
- Theo dõi đơn mua
  - Trạng thái đơn hàng: đang xử lý, đang giao, đã giao...
  - Cho phép hủy đơn với các đơn ở tình trạng đang xử lý, chờ xác nhận.
  

## 🧑‍💻 Công nghệ sử dụng

| Layer         | Công nghệ                                  |
|---------------|--------------------------------------------|
| Frontend      | React Native (Expo), React Navigation      |
| Backend       | Node.js, Express                           |
| Cơ sở dữ liệu | SQL Server                                 |
| Authentication| JWT (JSON Web Token)                       |
| Dev Tool      | VS Code, SSMS 2014                         |



## 2.🗂️ Thiết kế cơ sở dữ liệu
Ứng dụng sử dụng cơ sở dữ liệu quan hệ MySQL để lưu trữ thông tin sản phẩm, người dùng, đơn hàng và các thành phần liên quan. Dữ liệu được tổ chức dưới dạng các bảng với các mối quan hệ rõ ràng, đảm bảo tính toàn vẹn và hiệu quả khi truy xuất.
### 🧩 Sơ đồ cơ sở dữ liệu (ERD)
Hình dưới đây thể hiện sơ đồ các bảng chính và mối quan hệ giữa chúng:
<img width="575" alt="DbDiagramDADNT" src="https://github.com/user-attachments/assets/4975d13a-6a7d-438d-97cb-24916f537732" />

Giải thích các bảng:
- TAIKHOAN: Lưu thông tin người dùng như tên đăng nhập, mật khẩu, số điện thoại, họ tên, địa chỉ,...
- DOAN: Danh sách sản phẩm gồm Id đồ ăn, tên, hình ảnh, giá, mô tả, loại.
- DONHANG: Đại diện cho một đơn hàng, liên kết với người dùng và chứa thông tin Id đơn hàng, tình trạng đơn, tổng tiền, tên đăng nhập và ngày đật.
- DONHANG_DOAN: Chi tiết đơn hàng, mỗi dòng tương ứng một sản phẩm trong đơn hàng chứa Id đơn hàng, Id đồ ăn và số lượng.
- GIOHANG: Lưu Id giỏ hàng, tên đăng nhập và tổng tiền
- GIOHANG_DOAN: Lưu sản phẩm mà người dùng thêm vào giỏ hàng chứa Id giỏ hàng, Id đồ ăn, số lượng.

## 3.⚙️ Chạy ứng dụng
### B1: Chạy cơ sở dữ liệu (SQL Server)
Vào file AppDatDoAn.sql chạy để khởi tạo cơ sở dữ liệu.

### B2: Kết nối với cơ sở dữ liệu 
Vào thư mục backend --> .env để chỉnh cấu hình kết nối với database
Sau đó ở thư mục backend "node server" để kết nối với server

<img width="397" alt="29-5 env" src="https://github.com/user-attachments/assets/bf85fbbf-193a-4f40-adfc-a3f61ec0d619" />

### B3: Kết nối frontend và backend
Vào thư mục api --> apiConfig.js chỉnh sửa URLServer thành "http://{địa chỉ IPv4 Address của máy mình}:5000"

<img width="470" alt="29-5 apiconfig" src="https://github.com/user-attachments/assets/b22539ef-f172-4f79-823f-7e8f79f458e0" />

Chạy "npx expo start" sử dụng ứng dụng expo go trên điện thoại kết nối (sử dụng chung mạng với máy tính).

## 4.🖼️ Một số hình ảnh của app
<img width="200" alt="login" src="https://github.com/user-attachments/assets/7e4b1102-36c1-4145-8830-264d9f2f2ae1" /> <img width="200" alt="register" src="https://github.com/user-attachments/assets/abc9e437-ebb1-472c-8fa1-87fae564d939" />
<img width="200" alt="home" src="https://github.com/user-attachments/assets/bd135c17-31a5-4949-b08b-727000498b0b" /> <img width="200" alt="detailproduct" src="https://github.com/user-attachments/assets/255df8ef-d409-4ef2-ac16-5ebd1785603f" />
<img width="200" alt="profile" src="https://github.com/user-attachments/assets/414a3ec5-6f1f-494d-a4e4-3b7b79a7fbab" /> <img width="200" alt="cart" src="https://github.com/user-attachments/assets/d461d60f-b87e-4593-8e76-16a8d82817ca" />
<img width="200" alt="ordershistory" src="https://github.com/user-attachments/assets/4883763f-26f0-4752-8a57-8f6ffe7765ed" /> <img width="200" alt="orderdetail" src="https://github.com/user-attachments/assets/1838809d-d127-493f-9f94-81f988c1c542" />

## 5.✅ Test case
Dữ liệu được ghi chứ ở trong file TestCase.xlxs.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

© 2025 [Nhóm 7 Đồ án Đa nền tảng 67CS2].





