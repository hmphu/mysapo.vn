# Kiểm hàng

[1. Lấy đơn kiểm hàng theo bộ lọc](#get-stock_adjustments?)

[2. Lấy ra một đơn kiểm hàng](#get-stock_adjustments_id)

[3. Lấy mã code đơn kiểm hàng](#get-stock_adjustments_codes)

[4. Hủy đơn kiểm hàng](#cancel-stock_adjustments)

[5. Cập nhật một đơn kiểm hàng ](#put-stock_adjustments_id)

[6. Thêm mới một đơn kiểm hàng ](#add-stock_adjustments_id)

[7. Cập nhật trạng thái đơn kiểm hàng ](#put-stock_adjustments_id_status)

**Các tham số**

<a name= "get-stock_adjustments?"></a>
## 1. Lấy đơn kiểm hàng theo bộ lọc
**Request**

```
GET admin/stock_adjustments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "get-stock_adjustments_id"></a>
## 2. Lấy ra một đơn kiểm hàng
**Request**
```
GET admin/stock_adjustments/{id}} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
```

<a name= "get-stock_adjustments_codes"></a>
## 3. Lấy mã code đơn kiểm hàng

**Request**
```
POST admin/stock_adjustments/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "cancel-stock_adjustments"></a>
## 4. Hủy đơn kiểm hàng
**Request**
```
POST admin/stock_adjustments/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name="put-stock_adjustments_id"></a>
## 5. Cập nhật một đơn kiểm hàng 

**Request**
```
PUT admin/stock_adjustments/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

params: statuses = draft
```
**Kết quả trả về**
```

```
<a name="add-stock_adjustments_id"></a>
## 6. Thêm mới một đơn kiểm hàng

**Request**
```
POST admin/stock_adjustments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
status=draft

```
**Kết quả trả về**
```
Status 200 OK
```
**Trường hợp có lỗi**
```

```
<a name="put-stock_adjustments_id_status"></a>
## 7. Cập nhật trạng thái đơn kiểm hàng
**Request**
```
PUT admin/stock_adjustments/{id}/{status} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
status=draft

```
**Kết quả trả về**
```
Status 200 OK
```
**Trường hợp có lỗi**
```

```

