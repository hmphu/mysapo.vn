# OrderReturn

## Thêm 1 đơn trả hàng

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------|:-------------|
| OrderReturn.id | no | Mã tham chiếu đơn trả hàng |
| OrderReturn.tenant_id | no |  |
| OrderReturn.location_id | no |  |
| OrderReturn.code | no | Mã tham chiếu của khách hàng có đơn hàng |
| OrderReturn.account_id | no | Id định danh tài khoản nhân viên dùng để tạo đơn hàng |
| OrderReturn.order_id | yes |  |
| OrderReturn.order_code | no |  |
| OrderReturn.customer_id | no |  |
| OrderReturn.billing_address | no |  |
| OrderReturn.contact_id | no |  |
| OrderReturn.reference| no |  |
| OrderReturn.status| no |  |
| OrderReturn.refund_status| no |  |
| OrderReturn.total_amount | no |  |
| OrderReturn.issued_on | no | Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. Thuộc tính này được tạo tự động và không thể chỉnh sửa. Nếu bạn import Order từ một hệ thống khác vào Sapo thì hãy sử dụng thuộc tính có thể ghi processed_on để xác định thời gian Order được xử lý. |
| OrderReturn.received_on | no |  |
| OrderReturn.created_on| no |  |
| OrderReturn.refund_status| no |  |
| OrderReturn.modified_on | no |  |
| OrderReturn.line_items | yes |  |

**Request**
```
POST /admin/order_returns HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "order_return": {
    "id": 1635,
    "tenant_id": 77,
    "location_id": 81,
    "code": "SR1810161",
    "account_id": 33,
    "order_id": 7859,
    "order_code": null,
    "customer_id": 10080,
    "billing_address": null,
    "contact_id": null,
    "reference": null,
    "note": null,
    "status": "returning",
    "refund_status": "partial",
    "total_amount": 10000,
    "issued_on": "2016-10-18T08:54:16Z",
    "received_on": null,
    "created_on": "2016-10-18T08:54:16Z",
    "modified_on": "2016-10-18T08:54:43Z",
    "line_items": [
      {
        "id": 2074,
        "product_id": 27970,
        "product_name": "Hoa lay ơn trắng",
        "variant_id": 34198,
        "variant_name": "Hoa lay ơn trắng",
        "note": null,
        "quantity": 1,
        "price": 10000,
        "is_composite": false,
        "is_freeform": false,
        "line_amount": 10000,
        "created_on": "2016-10-18T08:54:16Z",
        "modified_on": "2016-10-18T08:54:16Z"
      }
    ]
  }
}
```
**Kết quả trả về**
```
{
  "order_return": {
    "id": 1635,
    "tenant_id": 77,
    "location_id": 81,
    "code": "SR1810161",
    "account_id": 33,
    "order_id": 7859,
    "order_code": null,
    "customer_id": 10080,
    "billing_address": null,
    "contact_id": null,
    "reference": null,
    "note": null,
    "status": "returning",
    "refund_status": "partial",
    "total_amount": 10000,
    "issued_on": "2016-10-18T08:54:16Z",
    "received_on": null,
    "created_on": "2016-10-18T08:54:16Z",
    "modified_on": "2016-10-18T08:54:43Z",
    "line_items": [
      {
        "id": 2074,
        "product_id": 27970,
        "product_name": "Hoa lay ơn trắng",
        "variant_id": 34198,
        "variant_name": "Hoa lay ơn trắng",
        "note": null,
        "quantity": 1,
        "price": 10000,
        "is_composite": false,
        "is_freeform": false,
        "line_amount": 10000,
        "created_on": "2016-10-18T08:54:16Z",
        "modified_on": "2016-10-18T08:54:16Z"
      }
    ]
  }
}
```
**Trường hợp có lỗi**
```

```
## Tạo mới code cho đơn trả hàng
```
POST /admin/order_returns/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
{
    "order_return_code": {
        "tenant_id": 56322,
        "code": "SR2906182"
    }
}
```
## Lấy một đơn trả hàng theo id
```
GET /admin/order_returns/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
{
    "order_return": {
        "id": 198300,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SR2906181",
        "account_id": 72098,
        "order_id": 14549649,
        "order_code": "SO1806182",
        "customer_id": 3335156,
        "billing_address": {
            "id": 17662926,
            "label": null,
            "first_name": "Thoa",
            "last_name": "Đào",
            "address1": "Trương Định",
            "address2": null,
            "email": null,
            "phone_number": "01647158965",
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Quận Hoàng Mai",
            "zip_code": null,
            "full_address": null
        },
        "contact_id": null,
        "reference": null,
        "note": null,
        "status": "returning",
        "refund_status": "unpaid",
        "total_amount": 1999980,
        "total_quantity": null,
        "issued_on": "2018-06-29T03:49:26Z",
        "received_on": null,
        "created_on": "2018-06-29T03:49:36Z",
        "modified_on": "2018-06-29T03:49:36Z",
        "line_items": [
            {
                "id": 371591,
                "order_line_item_id": 22887065,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_id": 4653239,
                "variant_name": "Áo khoác có mũ Bellfield",
                "note": null,
                "quantity": 2,
                "price": 999990,
                "is_composite": false,
                "is_freeform": false,
                "line_amount": 1999980,
                "created_on": "2018-06-29T03:49:36Z",
                "modified_on": "2018-06-29T03:49:36Z",
                "sku": "SP3",
                "barcode": "SP3",
                "unit": null,
                "variant_options": "Mặc định"
            }
        ],
        "refunds": [],
        "reason_id": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Không tìm thấy đơn trả"
    }
}
```
## Lấy đơn trả hàng theo bộ lọc
```
GET /admin/order_returns HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```

```
## Tạo yêu cầu Hủy 1 đơn trả hàng theo id
```
POST /admin/order_returns/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```

```
