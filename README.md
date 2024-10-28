# Hướng dẫn sử dụng GitHub cơ bản

## I. Giới thiệu chung về GitHub

### 1. GitHub là gì?

GitHub là một dịch vụ lưu trữ mã nguồn (source code) trực tuyến dựa trên nền tảng Git. Nó cung cấp một nền tảng cho các nhà phát triển để phát triển, quản lý và theo dõi mã nguồn của dự án phần mềm. Dịch vụ này cho phép các nhóm phát triển làm việc cùng nhau trên các dự án từ xa và theo dõi lịch sử của mã nguồn.

### 2. Một vài khái niệm của Git bạn cần nắm

- **Repository**: Kho quản lý dữ liệu, là nơi lưu trữ các dữ liệu, mã nguồn của project.
- **Git**: Là tiền tố của các lệnh được sử dụng trên giao diện dòng lệnh (CLI).
- **Branch (nhánh)**: Là cơ chế giúp quản lý các phiên bản khác nhau của mã nguồn trong cùng một kho lưu trữ (repository). Mỗi branch đại diện cho một dòng phát triển riêng biệt của dự án, cho phép bạn làm việc trên các tính năng, sửa lỗi hoặc thử nghiệm ý tưởng mới mà không ảnh hưởng đến mã nguồn chính (thường được lưu trữ trên branch `main` hoặc `master`).
- **Clone**: Là lệnh được sử dụng để tạo ra một bản sao của một kho lưu trữ từ một máy chủ về máy tính cục bộ.
- **Commit**: Lưu lại các thay đổi trong mã nguồn vào kho lưu trữ. Mỗi commit giống như một điểm chụp lại trạng thái hiện tại của mã nguồn tại một thời điểm cụ thể.
- **Push**: Là thao tác để đẩy các thay đổi từ repository cục bộ lên repository trên máy chủ.
- **Pull**: Lệnh này giúp bạn lấy về (fetch) và hợp nhất (merge) các thay đổi mới nhất từ một nhánh trên remote.
- **.gitignore**: File được sử dụng để loại bỏ các thư mục, file mà mình không muốn push lên máy chủ Git.

---

### 3. Cài đặt Git

Hai điều đầu tiên bạn cần làm là cài đặt git và tạo một tài khoản GitHub miễn phí.
Để cài Git hãy làm theo hướng dẫn [tại đây](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) (nếu chưa cài đặt). Lưu ý rằng đối với hướng dẫn này, chúng ta sẽ chỉ sử dụng git trên dòng lệnh. Mặc dù có một số GUI git (giao diện người dùng đồ họa) tuyệt vời, tôi nghĩ rằng sẽ dễ dàng hơn khi học git bằng các lệnh dành riêng cho git trước rồi sau đó thử GUI git khi bạn đã quen với lệnh hơn.

## II. Hướng dẫn sử dụng GitHub

### 1. Tạo tài khoản

- **Bước 1**: Truy cập [GitHub](https://github.com/) và chọn **Sign up**.
- **Bước 2**: Nhập thông tin tài khoản email và mật khẩu, sau đó chọn **Continue**.
- **Bước 3**: Xác minh tài khoản để chứng minh là người thật.
  - Có 2 phương thức xác thực:
    - **Xác minh bằng hình ảnh**
    - **Xác thực bằng âm thanh**
- **Bước 4**: Sau khi hoàn tất xác minh người thật, bạn sẽ cần xác minh email. GitHub sẽ gửi một dãy số vào email của bạn, chỉ cần nhập vào để hoàn thành bước này.

---

### 2. Tạo SSH Key cho tài khoản

#### Tại sao nên dùng SSH key thay vì HTTPS khi khởi tạo repo và commit?

- Từ tháng 8/2021, GitHub không còn hỗ trợ xác thực bằng mật khẩu thông qua HTTPS mà yêu cầu sử dụng **Personal Access Token (PAT)**. Token này phải được tạo từ GitHub và thay thế mật khẩu. Nếu bạn chưa tạo và sử dụng token, thì push qua HTTPS sẽ không thành công.

#### SSH key là gì?

- SSH key là một cặp khóa mã hóa gồm một khóa công khai và một khóa bí mật. Chúng được sử dụng để xác thực bảo mật khi bạn kết nối với GitHub từ máy tính của mình mà không cần nhập mật khẩu mỗi lần truy cập.

#### Các bước cài đặt SSH key để liên kết tài khoản GitHub với máy tính

**Bước 1**: **Kiểm tra máy đã có SSH key chưa**

- Ở màn hình desktop, chuột phải chọn **Git Bash Here** và chạy lệnh:
  ```bash
  ls -al ~/.ssh
  ```
  Nếu thấy các file như `id_rsa` và `id_rsa.pub`, tức là bạn đã có SSH key. Nếu không cần tạo SSH key mới.

![Kết quả kiểm tra SSH key](public/image.png)

- Chạy lệnh sau để xem dãy key và coppy chúng:

```bash
cat ~/.ssh/id_rsa.pub
```

![](public/image2.png)
**Trường hợp trên máy chưa có key**

- chạy lệnh `ssh-keygen` nhấn enter
  coppy đường dẫn mở trên cửa sổ trình duyệt và coppy nội dung
  Vd: C:\Users\USER02/.ssh/id_rsa.pub

![](public/image3.png)

**Bước 2**: vào github chọn **setting** chọn **SSH and GPG key** chọn **New SSH key** nhập key đã coppy vào mục key và Nhấn **Add SSH key**

![](public/image4.png)
