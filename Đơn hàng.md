# Đơn hàng
## Đơn hàng mới
Đối tác gửi danh sách đơn hàng sang hệ thống của Sapo.vn thông qua APIs. Sau khi các đơn hàng được lưu thành công vào hệ thống của Sapo.vn, hệ thống sẽ trả về danh sách đơn hàng tương ứng chứa các thông tin liên quan của mỗi đơn hàng.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------|:-------------|
| Order.code | yes | Mã tham chiếu của khách hàng có đơn hàng |
| Order.issued_on |	yes | Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. Thuộc tính này được tạo tự động và không thể chỉnh sửa. Nếu bạn import Order từ một hệ thống khác vào Sapo thì hãy sử dụng thuộc tính có thể ghi processed_on để xác định thời gian Order được xử lý.|
|Order.ship_on | no | Mã tham chiếu của khách hàng tạo đơn hàng |
| Order.account_id | yes | Id định danh tài khoản nhân viên dùng để tạo đơn hàng |
| Order.assignee_id | yes | Id định danh tài khoản nhân viên phụ trách đơn hàng vừa được tạo |
| Order.customer_id | yes | Id định danh khách hàng có đơn hàng |
| Order.contact_id |	yes | Id định danh cho liên hệ với khách hàng |
| Order.billing_address |	yes | Địa chỉ khách ghi vào hóa đơn |
| Order.shipping_address |	yes | Địa chỉ ship hàng đến ghi vào hóa đơn |
| Order.email |	yes | Email khách hàng |
| Order.phone_number |	yes | Số điện thoại khách hàng |
| Order.reference_number|	no | Số điện thoại khác của khách hàng (nếu có) . Trường này có thể NULL |
| Order.tax_treatment |	no | Số thuế (nếu có). Trường này có thể NULL |
| Order.status |	yes | Trạng thái đơn hàng |
| Order.source_id |	yes | Id định danh cho nguồn hàng từ nhà cung cấp |
| Order.note |	no | Ghi chú cho đơn hàng. Trường này có thể NULL |
| Order.tags |	no | Gắn thẻ tags cho sản phẩm. Trường này có thể NULL |
| Order.delivery_fee|	yes | Số điện thoại khác của khách hàng (nếu có) . Trường này có thể NULL |
| Order.discount_items |	yes | Phí vận chuyển của đơn hàng |
| Order.promotion_items |	yes | Danh sách hàng khuyến mại |
| Order.expected_payment_method_id |	yes | Id định danh cho nguồn hàng từ nhà cung cấp |
| Order.expected_delivery_type |	yes |  |
| Order.expected_delivery_provider_id |	yes |  |
```
POST /admin/orders HTTP/1.1
Token: 
Content-Type: application/json
{
  "order": {
    "code": "SO14061729",
    "issued_on": "2017-06-14T16:43:21Z",
    "ship_on": null,
    "account_id": 5923,
    "assignee_id": 5923,
    "customer_id": 23003,
    "contact_id": 1,
    "billing_address": {
      "label": "địa chỉ ghi vào hóa đơn",
      "first_name": "Hồi",
      "last_name": "Nguyễn",
      "address1": "442 Đội Cung",
      "address2": "442 Đội Đá",
      "email": "hoinx01@gmail.com",
      "phone_number": "01293291430",
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Quận 2 Pà Tưng",
      "zip_code": "10000"
    },
    "shipping_address": {
      "label": "địa chỉ ghi vào hóa đơn",
      "first_name": "Hồi",
      "last_name": "Nguyễn",
      "address1": "444 Đội Cung",
      "address2": "442 Đội Đá",
      "email": "hoinx012@gmail.com",
      "phone_number": "01293291430",
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Quận 3 Pà Tưng",
      "zip_code": "10000"
    },
    "email": "hoinx02@gmail.com",
    "phone_number": "01293291430",
    "reference_number": "chả nhớ cái property này có ý nghĩa gì",
    "price_list_id": 11672,
    "tax_treatment": "inclusive",
    "status": "finalized",
    "source_id": 3449,
    "note": "note thì null cũng được",
    "tags": [
      "1",
      "hanoi",
      "hichic"
    ],
    "delivery_fee": {
      "shipping_cost_id": 1,
      "shipping_cost_name": "hihi",
      "fee": 20000
    },
    "discount_items": [
      {
        "position": 0,
        "source": "manual",
        "rate": 0,
        "value": 20000,
        "amount": 20000,
        "reason": null
      },
      {
        "position": 1,
        "source": "customer_default",
        "rate": 0,
        "value": 20000,
        "amount": 20000,
        "reason": null
      },
      {
        "position": 2,
        "source": "customer_loyalty",
        "rate": 0,
        "value": 20000,
        "amount": 20000,
        "reason": null
      },
      {
        "position": 3,
        "source": "promotion_program",
        "rate": 0,
        "value": 20000,
        "amount": 20000,
        "reason": null
      }
    ],
    "promotion_items": [
      {
        "discount_item_position": 3,
        "promotion_id": 1,
        "promotion_condition_item_id": 1,
        "promotion_item_id": 1,
        "item_type": "discount",
        "satisfy_entities": "order.this"
      }
    ],
    "order_line_items": [
      {
        "variant_id": 71743,
        "product_id": 59901,
        "product_name": "Tương ớt",
        "variant_name": "Tương ớt - cay nhất - to",
        "tax_type_id": 1,
        "tax_rate_override": 10,
        "note": null,
        "price": 234000,
        "quantity": 5,
        "is_freeform": false,
        "discount_items": [
          {
            "position": 0,
            "source": "manual",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          },
          {
            "position": 1,
            "source": "customer_default",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          },
          {
            "position": 2,
            "source": "customer_loyalty",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          },
          {
            "position": 3,
            "source": "promotion_program",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          }
        ],
        "promotion_items": [
          {
            "discount_item_position": 3,
            "promotion_id": 1,
            "promotion_condition_item_id": 1,
            "promotion_item_id": 1,
            "item_type": "discount",
            "satisfy_entities": "order.this"
          }
        ]
      },
      {
        "variant_id": 71743,
        "product_id": 59901,
        "product_name": "Tương ớt",
        "variant_name": "Tương ớt - cay nhất - to",
        "tax_type_id": 1,
        "tax_rate_override": 10,
        "note": null,
        "price": 234000,
        "quantity": 5,
        "is_freeform": false,
        "discount_items": [
          {
            "position": 0,
            "source": "manual",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          },
          {
            "position": 1,
            "source": "customer_default",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          },
          {
            "position": 2,
            "source": "customer_loyalty",
            "rate": 0,
            "value": 20000,
            "amount": 20000,
            "reason": null
          }
        ],
        "promotion_items": []
      }
    ],
    "expected_payment_method_id": 1,
    "expected_delivery_type": "pickup",
    "expected_delivery_provider_id": 1
  }
}
```
