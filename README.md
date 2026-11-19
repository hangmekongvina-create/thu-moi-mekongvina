# Website thư mời điện tử MêKông Vina — Bản GitHub Pages

Website thư mời điện tử sử dụng file PDF, có hiệu ứng lật trang 3D. Không cần Node.js, VPS hoặc máy chủ riêng.

## 1. Các chức năng
- Hoạt động trên GitHub Pages.
- Trang quản trị cho phép tải file PDF và nhạc nền lên trực tiếp kho mã nguồn GitHub thông qua GitHub Contents API.
- Tạo một đường link riêng cho từng thư mời để gửi cho khách.
- Hiển thị các trang PDF ngay trên trình duyệt bằng PDF.js và StPageFlip, kèm hiệu ứng lật trang.
- Có thể thêm nhạc nền, điều khiển chuyển trang, xem toàn màn hình và giao diện tương thích với điện thoại.

## 2. Những điều cần lưu ý
- GitHub Pages là dịch vụ lưu trữ website tĩnh, không cung cấp hệ thống quản trị riêng chạy trên máy chủ.
- Khi quản trị, bạn cần nhập GitHub Personal Access Token (mã truy cập cá nhân) dạng fine-grained vào trang quản trị. Mã này chỉ được giữ tạm trong bộ nhớ của trang, không được lưu vào mã nguồn hoặc bộ nhớ trình duyệt. Chỉ sử dụng trên thiết bị đáng tin cậy và thu hồi mã ngay nếu nghi ngờ bị lộ.
- Hãy tạo token chỉ có quyền truy cập vào đúng một repository và cấp quyền **Contents: Read and write**. Không cấp các quyền không cần thiết khác.
- Nếu repository GitHub được đặt ở chế độ công khai (public), các file thư mời và nhạc tải lên cũng có thể được mọi người truy cập. Không tải lên thư mời chứa thông tin bí mật hoặc dữ liệu cá nhân nhạy cảm.
- GitHub Contents API có giới hạn dung lượng và tần suất tải lên. Khuyến nghị file PDF dưới 20 MB và file âm thanh dưới 10 MB. Hãy nén file nếu dung lượng lớn hơn.
- Sau khi tải file lên, GitHub Pages có thể cần vài phút để cập nhật website.
- Website tải thư viện PDF.js và StPageFlip từ CDN nên thiết bị cần có kết nối Internet.

## 3. Hướng dẫn cài đặt

### Bước 1: Tạo repository trên GitHub
1. Đăng nhập GitHub và tạo một repository mới, ví dụ: `thu-moi`.
2. Để sử dụng GitHub Pages miễn phí theo cách cài đặt này, hãy chọn repository ở chế độ **Public**.

### Bước 2: Tải mã nguồn lên GitHub
1. Giải nén file ZIP dự án.
2. Tải toàn bộ file và thư mục bên trong lên thư mục gốc của repository vừa tạo.
3. Commit các thay đổi lên nhánh `main`.

### Bước 3: Cấu hình repository
Mở file `assets/config.js` và chỉnh sửa các thông tin sau:
- `owner`: tên người dùng GitHub hoặc tên tổ chức sở hữu repository.
- `repo`: tên repository, ví dụ `thu-moi`.
- `branch`: tên nhánh sử dụng, mặc định là `main` (hoặc nhánh bạn đã chọn).

Lưu file và commit thay đổi lên GitHub.

### Bước 4: Bật GitHub Pages
1. Mở repository trên GitHub.
2. Chọn **Settings → Pages**.
3. Trong mục **Build and deployment**, chọn **Deploy from a branch**.
4. Chọn nhánh `main` và thư mục `/(root)`, sau đó nhấn **Save**.
5. Chờ GitHub Pages tạo và hiển thị địa chỉ website.

### Bước 5: Mở trang quản trị
Truy cập đường dẫn website đã được GitHub Pages cấp, thêm `/admin.html` vào cuối địa chỉ.

Ví dụ: `https://TEN-GITHUB.github.io/thu-moi/admin.html`

### Bước 6: Tạo GitHub Token
1. Trên GitHub, vào **Settings → Developer settings → Personal access tokens → Fine-grained tokens**.
2. Chọn **Generate new token**.
3. **Resource owner**: chọn tài khoản hoặc tổ chức sở hữu repository.
4. **Repository access**: chọn **Only select repositories**, sau đó chọn đúng repository thư mời.
5. Trong **Repository permissions**, đặt quyền **Contents** thành **Read and write**.
6. Tạo token và sao chép mã vừa được cấp. GitHub thường chỉ hiển thị đầy đủ mã này một lần.

### Bước 7: Kết nối trang quản trị với GitHub
1. Trên trang `/admin.html`, nhập tên tài khoản/tổ chức (**owner**), tên repository (**repo**), nhánh (**branch**) và token vừa tạo.
2. Nhấn **Kiểm tra kết nối** để kiểm tra thông tin.
3. Không chia sẻ token cho người khác và không đưa token vào file mã nguồn.

### Bước 8: Tạo và gửi thư mời
1. Chọn file thư mời PDF cần đăng tải.
2. Nếu muốn, chọn thêm file nhạc nền MP3.
3. Nhấn **Xuất bản thư mời**.
4. Sao chép đường link được tạo và gửi cho khách mời.

## 4. Ví dụ đường dẫn
- Trang quản trị: `https://TEN-GITHUB.github.io/thu-moi/admin.html`
- Trang xem thư mời: `https://TEN-GITHUB.github.io/thu-moi/invite.html?id=ma-thu-moi`

Mỗi thư mời sẽ có một mã riêng trong đường dẫn. Hãy gửi đúng link tương ứng cho từng khách hoặc nhóm khách.

## 5. Quản lý và bảo mật
- File tải lên được lưu trong thư mục `invitations/<ma-thu-moi>/` của repository.
- Muốn xóa một thư mời, hãy xóa thư mục tương ứng trong repository GitHub.
- Không nhập GitHub Token trên máy tính công cộng. Nếu nghi ngờ token bị lộ, hãy vào phần cài đặt token trên GitHub để thu hồi (revoke) token đó và tạo token mới khi cần.
- Người cộng tác trong repository có quyền ghi (write) cũng có thể chỉnh sửa hoặc xóa các file thư mời.
