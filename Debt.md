# Công nợ
Dễ dàng đối chiếu khách hàng, nhà cung cấp còn đang nợ chủ shop.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------|:-------------|
| id | no | string - Mã tham chiếu của khách hàng có đơn hàng |
| code | no| string - . Thuộc tính này được tạo tự động và không thể chỉnh sửa. Nếu bạn import Order từ một hệ thống khác vào Sapo thì hãy sử dụng thuộc tính có thể ghi processed_on để xác định thời gian Order được xử lý.|
| account_name | no | string - Thời gian hẹn giao hàng |
| document_issued_on | no | datetime - Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601 |
| modified_on | no| datetime - Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601 |
| change_debt | no |  - Id định danh khách hàng có đơn hàng |
| debt_amount |	no |  - Id định danh cho liên hệ với khách hàng |
| location_id |	no | int - Địa chỉ khách ghi vào hóa đơn |
| account_id | no | int - Id định danh tài khoản nhân viên phụ trách đơn hàng vừa được tạo |
| created_on | no | datetime - Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601 |
| document_type | no | int - Id định danh cho liên hệ với khách hàng |
| document_id |	no | string - Địa chỉ khách ghi vào hóa đơn |
| object_type |	no | int - Id định danh cho liên hệ với khách hàng |
| object_id | no | string - Địa chỉ khách ghi vào hóa đơn |
| action | no | string - Id định danh tài khoản nhân viên phụ trách đơn hàng vừa được tạo |
| log_id | no | int - Id định danh khách hàng có đơn hàng |
| log_type | no | int - Id định danh cho liên hệ với khách hàng |
| root_id| no | int - id khách ghi vào hóa đơn |

[ 1.1 Lấy ra tổng nợ của một khách hàng ](#customers_id_debts)

[ 1.2 Lấy ra tổng nợ của một nhà cung cấp](#suppliers_id_debts)

[ 1.3 Lấy ra tất cả tổng đang nợ của một nhà cung cấp](#suppliers_id_debt_change_logs)

<a name="customers_id_debts"></a>
## Lấy ra tổng nợ của một khách hàng 
**Request**
```
GET /admin/customers/{id}/debts HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "debt": {
        "debt_amount": 693000
    }
}
```
<a name="suppliers_id_debts"></a>
## Lấy ra tổng nợ của một nhà cung cấp
**Request**
```
GET admin/suppliers/{id}/debts HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "debt": {
        "debt_amount": 17500000
    }
}
```
<a name="suppliers_id_debt_change_logs"></a>
## Lấy ra nhật ký tổng nợ của một nhà cung cấp
**Request**
```
GET admin/suppliers/{id}/debt_change_logs HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "metadata": {
        "total": 1,
        "page": 1,
        "limit": 250
    },
    "debt_change_logs": [
        {
            "id": 17030595,
            "code": "PO1807181",
            "invoice_code": null,
            "account_name": "Ha Duong",
            "document_issued_on": "2018-07-18T08:19:39Z",
            "modified_on": "2018-07-18T08:19:39Z",
            "change_debt": 17500000,
            "debt_amount": 17500000,
            "location_id": 58369,
            "account_id": 72098,
            "created_on": "2018-07-18T08:19:39Z",
            "document_type": 102,
            "document_id": 371937,
            "object_type": 0,
            "object_id": 4202926,
            "action": "bill_added",
            "log_id": 506371,
            "log_type": 1,
            "root_id": 506371
        }
    ]
}
```
