# Voucher
## 1. Phiếu chi
Chủ shop quản lý phiếu thu và phiếu chi của cửa hàng.
Phiếu chi là chứng từ kế toán bắt buộc dùng để xác định số tiền mặt thực tế nhập quỹ, làm bằng chứng cho việc đã thanh toán hay chưa.

### 1.1 Đăng phiếu chi

**Request**
```
POST /admin/payment_vouchers HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "payment_voucher": {
    "id": 4,
    "tenant_id": 77,
    "location_id": 81,
    "account_id": 0,
    "code": "PV1307164",
    "object_type": "customer",
    "object_id": "1381",
    "issued_on": "2016-07-13T01:59:35Z",
    "reference": "refrrrrrrrrrrrrrrrrrrr",
    "note": "Piếu này đã sửa",
    "payment_method_id": 2008,
    "currency_id": 7030,
    "exchange_rate": 0,
    "amount": 9000,
    "source_type": null,
    "source_id": null,
    "type": "payment",
    "auto": false,
    "counted": true,
    "status": "cancelled",
    "created_on": "2016-07-13T02:00:02Z",
    "modified_on": "2016-07-13T02:12:31Z",
    "tags": [
      "hoinx",
      "haha091",
      "hichic"
    ]
  }
}
```
**Kết quả trả về khi đăng chứng từ thanh toán thành công**
```
{
  "payment_voucher": {
    "id": 4,
    "tenant_id": 77,
    "location_id": 81,
    "account_id": 0,
    "code": "PV1307164",
    "object_type": "customer",
    "object_id": "1381",
    "issued_on": "2016-07-13T01:59:35Z",
    "reference": "refrrrrrrrrrrrrrrrrrrr",
    "note": "Piếu này đã sửa",
    "payment_method_id": 2008,
    "currency_id": 7030,
    "exchange_rate": 0,
    "amount": 9000,
    "source_type": null,
    "source_id": null,
    "type": "payment",
    "auto": false,
    "counted": true,
    "status": "cancelled",
    "created_on": "2016-07-13T02:00:02Z",
    "modified_on": "2016-07-13T02:12:31Z",
    "tags": [
      "hoinx",
      "haha091",
      "hichic"
    ]
  }
}
```
**Trường hợp có lỗi**
```
```
### 1.2 Lấy phiếu chi theo id
**Request**

```
GET /admin/payment_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
```
**Trường hợp có lỗi**

```
```
### 1.3 Cập nhật phiếu chi
**Request**

```
PUT /admin/payment_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
```
**Trường hợp có lỗi**

```
```
### 1.4 Hủy phiếu chi
**Request**

```
POST /admin/payment_vouchers/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
```
**Trường hợp có lỗi**

```
```
### 1.5 Lấy phiếu chi theo bộ lọc
**Request**

```
GET /admin/payment_vouchers HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
```
**Trường hợp có lỗi**

```
```
