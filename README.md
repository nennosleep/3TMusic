# 3TMUSIC - Nền tảng Âm nhạc Trực tuyến 🎵

Dự án 3TMUSIC là một nền tảng âm nhạc trực tuyến chính thức, cung cấp tính năng quản lý bài hát, nghệ sĩ, thể loại, phân tích cảm xúc bài hát bằng AI.

Đây là kho lưu trữ tổng (Monorepo) chứa mã nguồn của cả **Backend**, **Frontend** và các cấu hình **Docker** để triển khai toàn bộ hệ thống.

## 📁 Cấu trúc dự án

- `WebNhac_FE/`: Mã nguồn giao diện người dùng (React.js, Vite, TailwindCSS).
- `WebNhac_BE/`: Mã nguồn máy chủ API (Node.js) và các cấu hình triển khai Docker (`docker-compose.yml`, CSDL, script AI...).

## 🛠 Yêu cầu hệ thống

Trước khi bắt đầu, hãy đảm bảo máy tính của bạn đã cài đặt:
- **[Git](https://git-scm.com/downloads)**
- **[Docker Desktop](https://www.docker.com/products/docker-desktop/)** (phải đang ở trạng thái **Running**).

## 🚀 Hướng dẫn cài đặt và khởi chạy (Docker)

Hệ thống đã được cấu hình sẵn để chạy trọn gói (Database + Backend + Frontend) thông qua Docker. 

### Bước 1: Clone dự án về máy

Mở Terminal (Command Prompt / PowerShell / Git Bash) và chạy lệnh:

```bash
git clone https://github.com/nennosleep/3TMusic.git
cd 3TMusic
```

### Bước 2: Chạy dự án (Run the Project)

Di chuyển vào thư mục **Backend** (vì file cấu hình `docker-compose.yml` nằm ở đây) và chạy lệnh khởi động:

```bash
cd WebNhac_BE
docker-compose up -d --build
```

**Quá trình khởi chạy sẽ thực hiện:**
1. Khởi tạo **Cơ sở dữ liệu MySQL** (Port `3307`), nạp tự động file `init.sql` để tạo các bảng và dữ liệu mẫu.
2. Build và chạy **Node.js Backend** (Port `3000`).
3. Build và chạy **React Frontend** (Port `5173`).

*(Lưu ý: Quá trình build lần đầu có thể mất vài phút tùy tốc độ mạng máy tính. Database cũng cần khoảng 10-20 giây để khởi động hoàn toàn trong lần đầu chạy).*

---

## 🌐 Các đường dẫn truy cập (Access URLs)

Sau khi quá trình chạy hoàn tất, hãy mở trình duyệt và truy cập:

- **Frontend (Giao diện người dùng / Admin):**  
  👉 [http://localhost:5173](http://localhost:5173)

- **Backend (API Base URL):**  
  👉 [http://localhost:3000/api](http://localhost:3000/api)

### Tài khoản mặc định để kiểm tra
- Role `1`: Người dùng (User) - Được đề xuất nhạc, quản lý playlist, nghe nhạc.
- Role `2`: Quản trị viên (Admin) - Có thể vào Dashboard quản trị bài hát, phân tích cảm xúc, quản lý user.

---

## 🛑 Cách dừng ứng dụng

Để tắt hệ thống mà không xóa dữ liệu, hãy đứng ở thư mục `WebNhac_BE` và chạy lệnh:
```bash
docker-compose stop
```

Để xóa hoàn toàn các container (dữ liệu trong database vẫn được giữ lại):
```bash
docker-compose down
```

## 🔧 (Tùy chọn) Chạy thủ công không dùng Docker

Nếu bạn muốn chạy Frontend hoặc Backend độc lập để code, bạn có thể vào từng thư mục (`WebNhac_FE` hoặc `WebNhac_BE`), chạy lệnh:
```bash
npm install
npm run dev
```
*(Đối với Backend, bạn vẫn cần tự thiết lập một database MySQL riêng hoặc chạy MySQL qua Docker).*
