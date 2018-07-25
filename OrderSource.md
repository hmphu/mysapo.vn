# Kênh bán hàng
Nếu bán hàng tại cửa hàng dùng màn hình pos mặc định là kênh POS
Còn khi chủ shop bán hàng online thì bắt buộc phải có kênh bán hàng.

## 1. Lấy một đối tượng kênh bán hàng
**Request**
```
GET /admin/order_sources/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```
```
## 2. Thêm một kênh bán hàng
**Request**
```
POST /admin/order_sources HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```
```
## 3. Sửa một kênh bán hàng
**Request**
```
PUT /admin/order_sources/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```
```
## 4. Xoá kênh bán hàng
**Request**
```
DELETE /admin/order_sources/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```
```
## 5. Lấy kênh bán hàng theo bộ lọc
**Request**
```
GET /admin/order_sources HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```
```
