# MyMiniCloud

MyMiniCloud là đề tài xây dựng một hệ thống cloud mini bằng Docker Compose. Hệ thống mô phỏng cách các dịch vụ trong môi trường cloud hoạt động cùng nhau, bao gồm giao diện web, backend API, cơ sở dữ liệu, xác thực người dùng, lưu trữ object, DNS nội bộ, giám sát hệ thống và API gateway.

Mục tiêu của đề tài là thực hành triển khai nhiều container độc lập, kết nối các service qua mạng nội bộ, cấu hình reverse proxy, load balancing, authentication và monitoring trong một hệ thống hoàn chỉnh.

## Thành viên

- Nguyễn Thị Anh Thư - 523H0100
- Lê Nhật Huy - 523H0138

## Công nghệ sử dụng

- Docker Compose
- Nginx
- Flask
- MariaDB
- Keycloak
- MinIO
- BIND9 DNS
- Prometheus
- Grafana

## Các service chính

| Service | Vai trò | Port |
| --- | --- | --- |
| `api-gateway-proxy-server` | Gateway Nginx | `80` |
| `web-frontend-server` | Frontend chính | `8080` |
| `application-backend-server` | Backend Flask API | `8085` |
| `relational-database-server` | MariaDB | `3306` |
| `authentication-identity-server` | Keycloak | `8081` |
| `object-storage-server` | MinIO | `9000`, `9001` |
| `internal-dns-server` | DNS nội bộ | `1053/udp` |
| `monitoring-prometheus-server` | Prometheus | `9090` |
| `monitoring-grafana-dashboard-server` | Grafana | `3000` |

## Cách chạy

```bash
git clone https://github.com/anhthu09205/523H0100_523H0138.git
cd 523H0100_523H0138
docker compose up -d --build
```

Kiểm tra container:

```bash
docker compose ps
```

Dừng hệ thống:

```bash
docker compose down
```

## Link truy cập

| Chức năng | URL |
| --- | --- |
| Trang chính | `http://localhost/` |
| Frontend trực tiếp | `http://localhost:8080/` |
| Blog | `http://localhost/blog/` |
| API hello | `http://localhost/api/hello` |
| Sinh viên từ JSON | `http://localhost/api/student` |
| Sinh viên từ MariaDB | `http://localhost/api/students-db` |
| Load balancing demo | `http://localhost/lb/` |
| Keycloak | `http://localhost:8081/` |
| MinIO Console | `http://localhost:9001/` |
| Prometheus | `http://localhost:9090/` |
| Grafana | `http://localhost:3000/` |

## API chính

- `GET /api/hello`: kiểm tra backend.
- `GET /api/blog`: lấy danh sách blog.
- `POST /api/blog`: tạo blog mới.
- `PUT /api/blog/<id>`: sửa blog.
- `DELETE /api/blog/<id>`: xóa blog.
- `GET /api/student`: lấy sinh viên từ file JSON.
- `GET /api/students-db`: lấy sinh viên từ MariaDB.
- `GET /api/secure`: API yêu cầu token Keycloak.

## Tài khoản mặc định

| Dịch vụ | Username | Password |
| --- | --- | --- |
| Keycloak | `admin` | `admin` |
| MinIO | `minioadmin` | `minioadmin` |
| MariaDB | `root` | `root` |
| Grafana | `admin` | `admin` |
