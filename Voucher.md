# Voucher
[1. Phiếu chi](#payment_vouchers)

  [1.1 Đăng phiếu chi](#add-payment_vouchers)
   
  [1.2 Lấy phiếu chi theo id](#get-payment_vouchers_id)

  [1.3 Lấy mã code phiếu chi](#get-payment_vouchers_codes)

  [1.4 Cập nhật phiếu chi](#put-payment_vouchers_id)

  [1.5 Hủy phiếu chi](#payment_vouchers_id-cancel)

  [1.6 Lấy phiếu chi theo bộ lọc](#get-payment_vouchers?)
  
[1. Phiếu thu](#receipt_vouchers)

  [1.1 Đăng phiếu thu](#add-receipt_vouchers)
   
  [1.2 Lấy phiếu thu theo id](#get-receipt_vouchers_id)

  [1.3 Lấy mã code phiếu thu](#get-receipt_vouchers_codes)

  [1.4 Cập nhật phiếu thu](#put-receipt_vouchers_id)

  [1.5 Hủy phiếu thu](#receipt_vouchers_id-cancel)

  [1.6 Lấy phiếu thu theo bộ lọc](#get-payment_vouchers?)
  
  
<a name="payment_vouchers"></a>
## 1. Phiếu chi
Chủ shop quản lý phiếu thu và phiếu chi của cửa hàng.
Phiếu chi là chứng từ kế toán bắt buộc dùng để xác định số tiền mặt thực tế nhập quỹ, làm bằng chứng cho việc đã thanh toán hay chưa.

<a name="get-payment_vouchers_id"></a>
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
<a name="get-payment_vouchers_id"></a>
### 1.2 Lấy phiếu chi theo id

**Request**
```
GET /admin/payment_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "Phiếu chi tự động tạo khi hoàn tiền cho khách trả hàng",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": "Tự động",
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-20T09:08:09Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Phiếu chi không tồn tại"
    }
}
```
<a name="get-payment_vouchers_codes"></a>
### 1.3 Lấy mã code phiếu chi

**Request**
```
GET /admin/payment_vouchers/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "Phiếu chi tự động tạo khi hoàn tiền cho khách trả hàng",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": "Tự động",
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-20T09:08:09Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Phiếu chi không tồn tại"
    }
}
```
<a name="put-payment_vouchers_id"></a>
### 1.4 Cập nhật phiếu chi
**Request**

```
PUT /admin/payment_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 

{"note": "abc"}
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "abc",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": null,
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-23T03:35:51Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Không tìm thấy đối tượng"
    }
}
```
<a name="payment_vouchers_id-cancel"></a>
### 1.5 Hủy phiếu chi
**Request**
```
POST /admin/payment_vouchers/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**
```
Status: 200 OK
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Không có quyền hoặc bị chặn thao tác"
    }
}
```
<a name="get-payment_vouchers?"></a>
### 1.6 Lấy phiếu chi theo bộ lọc

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
<a name="receipt_vouchers"></a>
## 1. Phiếu thu
Chủ shop quản lý phiếu thu và phiếu chi của cửa hàng.
Phiếu chi là chứng từ kế toán bắt buộc dùng để xác định số tiền mặt thực tế nhập quỹ, làm bằng chứng cho việc đã thanh toán hay chưa.

<a name="get-receipt_vouchers_id"></a>
### 1.1 Đăng phiếu thu

**Request**
```
POST /admin/receipt_vouchers HTTP/1.1
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
<a name="get-receipt_vouchers_id"></a>
### 1.2 Lấy phiếu thu theo id

**Request**
```
GET /admin/receipt_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "Phiếu chi tự động tạo khi hoàn tiền cho khách trả hàng",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": "Tự động",
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-20T09:08:09Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Phiếu chi không tồn tại"
    }
}
```
<a name="#get-receipt_vouchers_codes"></a>
### 1.3 Lấy mã code phiếu thu

**Request**
```
GET /admin/payment_vouchers/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "Phiếu chi tự động tạo khi hoàn tiền cho khách trả hàng",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": "Tự động",
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-20T09:08:09Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Phiếu chi không tồn tại"
    }
}
```
<a name="#put-payment_vouchers_id"></a>
### 1.4 Cập nhật phiếu thu
**Request**
```
PUT /admin/receipt_vouchers/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 

{"note": "abc"}
```
**Kết quả trả về**

```
{
    "payment_voucher": {
        "id": 7414112,
        "tenant_id": 56322,
        "location_id": 58369,
        "account_id": 72098,
        "code": "PV20071811",
        "object_type": "customer",
        "object_id": 3280093,
        "issued_on": "2016-06-30T11:06:29Z",
        "reference": null,
        "note": "abc",
        "payment_method_id": 220256,
        "currency_id": 0,
        "exchange_rate": 1,
        "amount": 10000,
        "source_type": "refund",
        "source_id": 159706,
        "group_id": 983501,
        "group_name": null,
        "auto": true,
        "counted": false,
        "status": "active",
        "created_on": "2018-07-20T09:08:09Z",
        "modified_on": "2018-07-23T03:35:51Z",
        "tags": [],
        "cancelled_on": null,
        "document_root_id": 212603,
        "document_root_code": "SR2007185",
        "account_name": null,
        "payment_method_name": null
    }
}
```
**Trường hợp có lỗi**

```
{
    "error": {
        "message": "Không tìm thấy đối tượng"
    }
}
```
<a name="#receipt_vouchers_id-cancel"></a>
### 1.5 Hủy phiếu thu
**Request**
```
POST /admin/receipt_vouchers/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**
```
Status: 200 OK
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Không có quyền hoặc bị chặn thao tác"
    }
}
```
<a name="#get-receipt_voucherss?"></a>
### 1.6 Lấy phiếu thu theo bộ lọc

**Request**
```
GET /admin/receipt_vouchers HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json 
```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**

```
```
