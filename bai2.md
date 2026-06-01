# Thiết kế REST API hệ thống mượn sách

## 1. Bảng thiết kế API

| Chức năng                           | Method | URL                 | Query params                              | Status thành công | Status lỗi      |
| ----------------------------------- | ------ | ------------------- | ----------------------------------------- | ----------------- | --------------- |
| Lấy danh sách sách                  | GET    | `/books`            | `?page=1&limit=10&author=Nguyễn Nhật Ánh` | 200 OK            | 400 Bad Request |
| Lấy chi tiết một sách               | GET    | `/books/{id}`       | Không có                                  | 200 OK            | 404 Not Found   |
| Thêm sách mới                       | POST   | `/books`            | Không có                                  | 201 Created       | 400 Bad Request |
| Cập nhật toàn bộ thông tin sách     | PUT    | `/books/{id}`       | Không có                                  | 200 OK            | 404 Not Found   |
| Cập nhật số lượng sách              | PATCH  | `/books/{id}`       | Không có                                  | 200 OK            | 400 Bad Request |
| Xóa sách                            | DELETE | `/books/{id}`       | Không có                                  | 204 No Content    | 404 Not Found   |
| Lấy danh sách thẻ mượn của một sách | GET    | `/books/{id}/loans` | `?page=1&limit=5`                         | 200 OK            | 404 Not Found   |
| Lấy tất cả thẻ mượn                 | GET    | `/loans`            | `?borrowerName=An`                        | 200 OK            | 400 Bad Request |
| Tạo thẻ mượn mới                    | POST   | `/loans`            | Không có                                  | 201 Created       | 400 Bad Request |
| Lấy chi tiết thẻ mượn               | GET    | `/loans/{id}`       | Không có                                  | 200 OK            | 404 Not Found   |
| Trả sách                            | PATCH  | `/loans/{id}`       | Không có                                  | 200 OK            | 404 Not Found   |
| Xóa thẻ mượn                        | DELETE | `/loans/{id}`       | Không có                                  | 204 No Content    | 404 Not Found   |

---

## 2. Ví dụ request

### 2.1. Lấy tất cả sách của tác giả Nguyễn Nhật Ánh

```http
GET /books?author=Nguyễn Nhật Ánh
```

---

### 2.2. Thêm sách mới

```http
POST /books
```

**Body:**

```json
{
  "title": "Mắt Biếc",
  "author": "Nguyễn Nhật Ánh",
  "year": 1990,
  "quantity": 10
}
```

---

### 2.3. Tạo thẻ mượn

```http
POST /loans
```

**Body:**

```json
{
  "bookId": 1,
  "borrowerName": "Nguyễn Văn A",
  "borrowDate": "2026-05-28"
}
```

---

### 2.4. Trả sách

```http
PATCH /loans/1
```

**Body:**

```json
{
  "returnDate": "2026-06-05"
}
```
