# Đơn hàng
## Đơn hàng mới
Đối tác gửi danh sách đơn hàng sang hệ thống của Sapo.vn thông qua APIs. Sau khi các đơn hàng được lưu thành công vào hệ thống của Sapo.vn, hệ thống sẽ trả về danh sách đơn hàng tương ứng chứa các thông tin liên quan của mỗi đơn hàng.

Bạn nên lưu ý rằng Order có thể được tạo qua API, nhưng thông tin thanh toán sẽ không được lưu trữ và không có một Transaction nào cả. Bạn có thể đánh dấu Order với bất kì trạng thái thanh toán nào.

Bạn cũng nên chú ý rằng bạn chỉ có thể thay đổi một vài thuộc tính của Order khi sử dụng API. Bạn không thể thay đổi item hay số lượng của item trong Order.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------|:-------------|
| Order.code | yes | string - Mã tham chiếu của khách hàng có đơn hàng |
| Order.issued_on |	yes | date - Thời gian Order được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. Thuộc tính này được tạo tự động và không thể chỉnh sửa. Nếu bạn import Order từ một hệ thống khác vào Sapo thì hãy sử dụng thuộc tính có thể ghi processed_on để xác định thời gian Order được xử lý.|
|Order.ship_on | no | date - Thời gian hẹn giao hàng |
| Order.account_id | yes | int - Id định danh tài khoản nhân viên dùng để tạo đơn hàng |
| Order.assignee_id | yes | int - Id định danh tài khoản nhân viên phụ trách đơn hàng vừa được tạo |
| Order.customer_id | yes | int - Id định danh khách hàng có đơn hàng |
| Order.contact_id |	yes | int - Id định danh cho liên hệ với khách hàng |
| Order.billing_address |	yes | string - Địa chỉ khách ghi vào hóa đơn |
| Order.shipping_address |	yes | string - Địa chỉ ship hàng đến ghi vào hóa đơn |
| Order.email |	yes | string - Email khách hàng |
| Order.phone_number |	yes | string - Số điện thoại khách hàng |
| Order.reference_number|	no | string - Số điện thoại khác của khách hàng (nếu có) . Trường này có thể NULL |
| Order.tax_treatment |	no | string - Số thuế (nếu có). Trường này có thể NULL |
| Order.status |	yes | string - Trạng thái đơn hàng |
| Order.source_id |	yes | int - Id định danh cho nguồn hàng từ nhà cung cấp |
| Order.note | no | string - Ghi chú cho đơn hàng. Trường này có thể NULL |
| Order.tags | no | string - Gắn thẻ tags cho sản phẩm. Trường này có thể NULL |
| Order.delivery_fee|	yes | string - Số điện thoại khác của khách hàng (nếu có) . Trường này có thể NULL |
| Order.discount_items | yes | objects - Phí vận chuyển của đơn hàng |
| Order.promotion_items |	yes | objects -	Danh sách hàng khuyến mại |
| Order.expected_payment_method_id | yes | int - Id định danh cho phương thức thanh toán |
| Order.expected_delivery_type | no | string - Loại đối tác giao hàng dự kiến (employee &  |
| Order.expected_delivery_provider_id |	no | string - Loại nhà cung cấp phân phối hàng dụ kiến |

**Request**
```
POST /admin/orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "order": {
    "id": 14894959,
    "tenant_id": 56322,
    "location_id": 58369,
    "code": "SO2606185",
    "created_on": "2018-06-26T02:01:04Z",
    "modified_on": "2018-06-26T03:15:23Z",
    "issued_on": "2018-06-26T02:01:05Z",
    "ship_on": null,
    "ship_on_min": null,
    "ship_on_max": null,
    "account_id": 72098,
    "assignee_id": 72098,
    "customer_id": 3689589,
    "contact_id": null,
    "billing_address": {
      "id": 17330171,
      "label": "",
      "first_name": null,
      "last_name": null,
      "address1": "Long Bien",
      "address2": null,
      "email": null,
      "phone_number": null,
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Quận Long Biên",
      "zip_code": null,
      "full_address": null
    },
    "shipping_address": {
      "id": 17330172,
      "label": "Giao hàng",
      "first_name": null,
      "last_name": null,
      "address1": "Gia lam",
      "address2": null,
      "email": null,
      "phone_number": null,
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Quận long Biên",
      "zip_code": null,
      "full_address": null
    },
    "email": null,
    "phone_number": "",
    "reference_number": null,
    "price_list_id": 167326,
    "tax_treatment": "exclusive",
    "status": "draft",
    "packed_status": "unpacked",
    "fulfillment_status": "unshipped",
    "received_status": "unreceived",
    "payment_status": "unpaid",
    "return_status": "unreturned",
    "source_id": 387299,
    "total": 800000,
    "order_discount_rate": 0,
    "order_discount_value": 0,
    "discount_reason": null,
    "total_discount": 0,
    "total_tax": 0,
    "note": null,
    "tags": [],
    "delivery_fee": null,
    "discount_items": [],
    "order_line_items": [
      {
        "id": 23638623,
        "created_on": "2018-06-26T02:01:04Z",
        "modified_on": "2018-06-26T03:15:23Z",
        "variant_id": 4697237,
        "product_id": 3262676,
        "product_name": "Áo khoác có mũ Bellfield",
        "variant_name": "Áo khoác có mũ Bellfield",
        "tax_type_id": null,
        "tax_included": false,
        "tax_rate_override": 0,
        "tax_rate": 0,
        "tax_amount": 0,
        "discount_rate": 0,
        "discount_value": 0,
        "discount_reason": null,
        "discount_amount": 0,
        "note": null,
        "price": 800000,
        "quantity": 1,
        "is_freeform": false,
        "is_composite": false,
        "line_amount": 800000,
        "discount_items": [],
        "sku": "SP10",
        "barcode": "SP10",
        "unit": null,
        "variant_options": "(combo)"
      }
    ],
    "prepayments": [],
    "fulfillments": [],
    "order_returns": [],
    "business_version": 2,
    "expected_payment_method_id": null,
    "expected_delivery_type": null,
    "expected_delivery_provider_id": null,
    "process_status_id": null,
    "reason_cancel_id": null,
    "finalized_on": null,
    "finished_on": null,
    "completed_on": null,
    "channel": null,
    "promotion_redemption_id": null,
    "promotion_name": null,
    "promotion_code": null
  }
}

```
**Kết quả trả về khi đăng đơn hàng thành công**
```
{
    "order": {
        "id": 14900216,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SO26061817",
        "created_on": "2018-06-26T04:35:16Z",
        "modified_on": "2018-06-26T04:35:16Z",
        "issued_on": "2018-06-26T02:01:05Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 72098,
        "customer_id": 3689589,
        "contact_id": null,
        "billing_address": {
            "id": 17339809,
            "label": "",
            "first_name": null,
            "last_name": null,
            "address1": "Long Bien",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Quận Long Biên",
            "zip_code": null,
            "full_address": null
        },
        "shipping_address": {
            "id": 17339810,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Gia lam",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Quận long Biên",
            "zip_code": null,
            "full_address": null
        },
        "email": null,
        "phone_number": "",
        "reference_number": null,
        "price_list_id": 167326,
        "tax_treatment": "exclusive",
        "status": "draft",
        "packed_status": "unpacked",
        "fulfillment_status": "unshipped",
        "received_status": "unreceived",
        "payment_status": "unpaid",
        "return_status": "unreturned",
        "source_id": 387299,
        "total": 800000,
        "order_discount_rate": 0,
        "order_discount_value": 0,
        "discount_reason": null,
        "total_discount": 0,
        "total_tax": 0,
        "note": null,
        "tags": [],
        "delivery_fee": null,
        "discount_items": [],
        "order_line_items": [
            {
                "id": 23650932,
                "created_on": "2018-06-26T04:35:16Z",
                "modified_on": "2018-06-26T04:35:16Z",
                "variant_id": 4697237,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_name": "Áo khoác có mũ Bellfield",
                "tax_type_id": null,
                "tax_included": false,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "tax_amount": 0,
                "discount_rate": 0,
                "discount_value": 0,
                "discount_reason": null,
                "discount_amount": 0,
                "note": null,
                "price": 800000,
                "quantity": 1,
                "is_freeform": false,
                "is_composite": false,
                "line_amount": 800000,
                "discount_items": [],
                "sku": "SP10",
                "barcode": "SP10",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "prepayments": [],
        "fulfillments": [],
        "order_returns": [],
        "business_version": 2,
        "expected_payment_method_id": null,
        "expected_delivery_type": null,
        "expected_delivery_provider_id": null,
        "process_status_id": null,
        "reason_cancel_id": null,
        "finalized_on": null,
        "finished_on": null,
        "completed_on": null,
        "channel": null,
        "promotion_redemption_id": null,
        "promotion_name": null,
        "promotion_code": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "shipping_address.address1": "may not be empty",
            "tax_treatment": "may not be null"
        }
    }
}
```
## Duyệt đơn hàng 
**Request**
```
POST /admin/orders/{id}/finalize HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi duyệt đơn hàng thành công**
```
{
    "order": {
        "id": 14900465,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SO26061820",
        "created_on": "2018-06-26T04:42:09Z",
        "modified_on": "2018-06-26T04:42:21Z",
        "issued_on": "2018-06-26T04:42:09Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 72098,
        "customer_id": 3281243,
        "contact_id": null,
        "billing_address": {
            "id": 17340293,
            "label": null,
            "first_name": "Hoàng Sơn",
            "last_name": "Nguyễn",
            "address1": "Tựu Liệt",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Thanh Trì",
            "zip_code": null,
            "full_address": null
        },
        "shipping_address": {
            "id": 17340294,
            "label": null,
            "first_name": "Hoàng Sơn",
            "last_name": "Nguyễn",
            "address1": "Tựu Liệt",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Thanh Trì",
            "zip_code": null,
            "full_address": null
        },
        "email": "ngocha.watchtime@gmail.com",
        "phone_number": null,
        "reference_number": null,
        "price_list_id": 167326,
        "tax_treatment": "exclusive",
        "status": "finalized",
        "packed_status": "unpacked",
        "fulfillment_status": "unshipped",
        "received_status": "unreceived",
        "payment_status": "unpaid",
        "return_status": "unreturned",
        "source_id": 387299,
        "total": 1400000,
        "order_discount_rate": 0,
        "order_discount_value": 0,
        "discount_reason": null,
        "total_discount": 0,
        "total_tax": 0,
        "note": null,
        "tags": [],
        "delivery_fee": null,
        "discount_items": [
            {
                "source": "manual",
                "rate": 0,
                "value": 0,
                "amount": 0,
                "reason": null
            }
        ],
        "order_line_items": [
            {
                "id": 23651451,
                "created_on": "2018-06-26T04:42:09Z",
                "modified_on": "2018-06-26T04:42:09Z",
                "variant_id": 4653234,
                "product_id": 3262674,
                "product_name": "Quần vải ống suông Farah",
                "variant_name": "Quần vải ống suông Farah",
                "tax_type_id": null,
                "tax_included": false,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "tax_amount": 0,
                "discount_rate": 0,
                "discount_value": 0,
                "discount_reason": null,
                "discount_amount": 0,
                "note": null,
                "price": 1400000,
                "quantity": 1,
                "is_freeform": false,
                "is_composite": false,
                "line_amount": 1400000,
                "discount_items": [
                    {
                        "source": "manual",
                        "rate": 0,
                        "value": 0,
                        "amount": 0,
                        "reason": null
                    }
                ],
                "sku": "SP2",
                "barcode": "SP2",
                "unit": null,
                "variant_options": "Mặc định"
            }
        ],
        "prepayments": [],
        "fulfillments": [],
        "order_returns": [],
        "business_version": 2,
        "expected_payment_method_id": null,
        "expected_delivery_type": null,
        "expected_delivery_provider_id": null,
        "process_status_id": null,
        "reason_cancel_id": null,
        "finalized_on": "2018-06-26T04:42:21Z",
        "finished_on": null,
        "completed_on": null,
        "channel": null,
        "promotion_redemption_id": null,
        "promotion_name": null,
        "promotion_code": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "": "Đơn hàng đã được xác nhận rồi"
        }
    }
}
```
## Hủy đơn hàng
**Request**
```
POST /admin/orders/ HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi hủy đơn hàng thành công**
```
{
    "order": {
        "id": 14895214,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SO26061812",
        "created_on": "2018-06-26T02:09:35Z",
        "modified_on": "2018-07-06T08:42:08Z",
        "issued_on": "2018-06-26T02:09:35Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 72098,
        "customer_id": 3689589,
        "contact_id": null,
        "billing_address": {
            "id": 17330610,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Gia lam",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Gia Lâm",
            "zip_code": null,
            "full_address": null
        },
        "shipping_address": {
            "id": 17330611,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Gia lam",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Gia Lâm",
            "zip_code": null,
            "full_address": null
        },
        "email": null,
        "phone_number": "01647019207",
        "reference_number": null,
        "price_list_id": 167326,
        "tax_treatment": "exclusive",
        "status": "cancelled",
        "packed_status": "unpacked",
        "fulfillment_status": "unshipped",
        "received_status": "unreceived",
        "payment_status": "unpaid",
        "return_status": "unreturned",
        "source_id": 387299,
        "total": 800000,
        "order_discount_rate": 0,
        "order_discount_value": 0,
        "discount_reason": null,
        "total_discount": 0,
        "total_tax": 0,
        "note": null,
        "tags": [],
        "delivery_fee": null,
        "discount_items": [
            {
                "source": "manual",
                "rate": 0,
                "value": 0,
                "amount": 0,
                "reason": null
            }
        ],
        "order_line_items": [
            {
                "id": 23639227,
                "created_on": "2018-06-26T02:09:35Z",
                "modified_on": "2018-06-26T02:09:35Z",
                "variant_id": 4697237,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_name": "Áo khoác có mũ Bellfield",
                "tax_type_id": null,
                "tax_included": false,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "tax_amount": 0,
                "discount_rate": 0,
                "discount_value": 0,
                "discount_reason": null,
                "discount_amount": 0,
                "note": null,
                "price": 800000,
                "quantity": 1,
                "is_freeform": false,
                "is_composite": false,
                "line_amount": 800000,
                "discount_items": [
                    {
                        "source": "manual",
                        "rate": 0,
                        "value": 0,
                        "amount": 0,
                        "reason": null
                    }
                ],
                "sku": "SP10",
                "barcode": "SP10",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "prepayments": [],
        "fulfillments": [],
        "order_returns": [],
        "business_version": 2,
        "expected_payment_method_id": null,
        "expected_delivery_type": null,
        "expected_delivery_provider_id": null,
        "process_status_id": null,
        "reason_cancel_id": null,
        "finalized_on": "2018-06-26T02:09:35Z",
        "finished_on": null,
        "completed_on": null,
        "channel": null,
        "promotion_redemption_id": null,
        "promotion_name": null,
        "promotion_code": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "": "Đơn hàng đã bị hủy"
        }
    }
}
```
## Hoàn thành đơn hàng
**Request**
```
POST /admin/orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi hoàn thành đơn hàng thành công**
```
{
    "order": {
        "id": 14895103,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SO2606188",
        "created_on": "2018-06-26T02:05:57Z",
        "modified_on": "2018-07-06T08:40:09Z",
        "issued_on": "2018-06-26T02:01:05Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 72098,
        "customer_id": 3689589,
        "contact_id": null,
        "billing_address": {
            "id": 17330419,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Gia lam",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Gia Lâm",
            "zip_code": null,
            "full_address": null
        },
        "shipping_address": {
            "id": 17330420,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Gia lam",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Gia Lâm",
            "zip_code": null,
            "full_address": null
        },
        "email": null,
        "phone_number": "01647019207",
        "reference_number": null,
        "price_list_id": 167326,
        "tax_treatment": "exclusive",
        "status": "finished",
        "packed_status": "unpacked",
        "fulfillment_status": "unshipped",
        "received_status": "unreceived",
        "payment_status": "unpaid",
        "return_status": "unreturned",
        "source_id": 387299,
        "total": 800000,
        "order_discount_rate": 0,
        "order_discount_value": 0,
        "discount_reason": null,
        "total_discount": 0,
        "total_tax": 0,
        "note": null,
        "tags": [],
        "delivery_fee": null,
        "discount_items": [
            {
                "source": "manual",
                "rate": 0,
                "value": 0,
                "amount": 0,
                "reason": null
            }
        ],
        "order_line_items": [
            {
                "id": 23638998,
                "created_on": "2018-06-26T02:05:57Z",
                "modified_on": "2018-06-26T02:05:57Z",
                "variant_id": 4697237,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_name": "Áo khoác có mũ Bellfield",
                "tax_type_id": null,
                "tax_included": false,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "tax_amount": 0,
                "discount_rate": 0,
                "discount_value": 0,
                "discount_reason": null,
                "discount_amount": 0,
                "note": null,
                "price": 800000,
                "quantity": 1,
                "is_freeform": false,
                "is_composite": false,
                "line_amount": 800000,
                "discount_items": [
                    {
                        "source": "manual",
                        "rate": 0,
                        "value": 0,
                        "amount": 0,
                        "reason": null
                    }
                ],
                "sku": "SP10",
                "barcode": "SP10",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "prepayments": [],
        "fulfillments": [],
        "order_returns": [],
        "business_version": 2,
        "expected_payment_method_id": null,
        "expected_delivery_type": null,
        "expected_delivery_provider_id": null,
        "process_status_id": null,
        "reason_cancel_id": null,
        "finalized_on": "2018-06-26T02:05:57Z",
        "finished_on": "2018-07-06T08:40:09Z",
        "completed_on": null,
        "channel": null,
        "promotion_redemption_id": null,
        "promotion_name": null,
        "promotion_code": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "": "Đơn hàng đã ở trạng thái ngừng thao tác"
        }
    }
}
{
    "data_error": {
        "status": 422,
        "errors": {
            "": "Không thể kết thúc đơn hàng đang ở trạng thái 'đặt hàng'"
        }
    }
}
```
## Sửa đơn hàng
**Request**
```
PUT /admin/orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi sửa đơn hàng thành công**
```

```
**Trường hợp có lỗi**
```

```
## Lấy danh sách đơn hàng
**Request**
```
GET/admin/orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi lấy danh sách đơn hàng thành công**
```
{
    "metadata": {
        "total": 38,
        "page": 1,
        "limit": 20
    }
```
## Lấy danh sách 1 đơn hàng theo id
**Request**
```
POST /admin/orders/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về khi đăng đơn thành công**
```
{
    "order": {
        "id": 14900465,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "SO26061820",
        "created_on": "2018-06-26T04:42:09Z",
        "modified_on": "2018-07-02T04:38:48Z",
        "issued_on": "2018-06-26T04:42:09Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 72098,
        "customer_id": 3281243,
        "contact_id": null,
        "billing_address": {
            "id": 17340293,
            "label": null,
            "first_name": "Hoàng Sơn",
            "last_name": "Nguyễn",
            "address1": "Tựu Liệt",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Thanh Trì",
            "zip_code": null,
            "full_address": null
        },
        "shipping_address": {
            "id": 17340294,
            "label": null,
            "first_name": "Hoàng Sơn",
            "last_name": "Nguyễn",
            "address1": "Tựu Liệt",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Huyện Thanh Trì",
            "zip_code": null,
            "full_address": null
        },
        "email": "ngocha.watchtime@gmail.com",
        "phone_number": null,
        "reference_number": null,
        "price_list_id": 167326,
        "tax_treatment": "exclusive",
        "status": "finalized",
        "packed_status": "packed",
        "fulfillment_status": "shipped",
        "received_status": "received",
        "payment_status": "unpaid",
        "return_status": "returned",
        "source_id": 387299,
        "total": 1400000,
        "order_discount_rate": 0,
        "order_discount_value": 0,
        "discount_reason": null,
        "total_discount": 0,
        "total_tax": 0,
        "note": null,
        "tags": [],
        "delivery_fee": null,
        "discount_items": [
            {
                "source": "manual",
                "rate": 0,
                "value": 0,
                "amount": 0,
                "reason": null
            }
        ],
        "order_line_items": [
            {
                "id": 23651451,
                "created_on": "2018-06-26T04:42:09Z",
                "modified_on": "2018-06-26T04:42:09Z",
                "variant_id": 4653234,
                "product_id": 3262674,
                "product_name": "Quần vải ống suông Farah",
                "variant_name": "Quần vải ống suông Farah",
                "tax_type_id": null,
                "tax_included": false,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "tax_amount": 0,
                "discount_rate": 0,
                "discount_value": 0,
                "discount_reason": null,
                "discount_amount": 0,
                "note": null,
                "price": 1400000,
                "quantity": 1,
                "is_freeform": false,
                "is_composite": false,
                "line_amount": 1400000,
                "discount_items": [
                    {
                        "source": "manual",
                        "rate": 0,
                        "value": 0,
                        "amount": 0,
                        "reason": null
                    }
                ],
                "sku": "SP2",
                "barcode": "SP2",
                "unit": null,
                "variant_options": "Mặc định"
            }
        ],
        "prepayments": [],
        "fulfillments": [
            {
                "id": 33444600,
                "tenant_id": 56322,
                "stock_location_id": 58369,
                "code": "FU0207182",
                "order_id": 14900465,
                "account_id": 72098,
                "assignee_id": 72098,
                "partner_id": 3281243,
                "billing_address": {
                    "id": 17978055,
                    "label": null,
                    "first_name": "Nguyễn Hoàng Sơn",
                    "last_name": "Nguyễn",
                    "address1": "Tựu Liệt",
                    "address2": null,
                    "email": null,
                    "phone_number": null,
                    "country": "Việt Nam",
                    "city": "Hà Nội",
                    "district": "Huyện Thanh Trì",
                    "zip_code": null,
                    "full_address": null
                },
                "delivery_type": "pickup",
                "tax_treatment": "exclusive",
                "discount_rate": 0,
                "discount_value": 0,
                "discount_amount": 0,
                "total": 1400000,
                "total_tax": 0,
                "total_discount": 0,
                "notes": null,
                "packed_on": "2018-07-02T04:36:04Z",
                "received_on": "2018-07-02T04:36:08Z",
                "shipped_on": "2018-07-02T04:36:08Z",
                "cancel_date": null,
                "cancel_account_id": null,
                "created_on": "2018-07-02T04:36:03Z",
                "modified_on": "2018-07-02T04:36:08Z",
                "status": "received",
                "composite_fulfillment_status": "received",
                "payment_status": "unpaid",
                "stock_out_account_id": 72098,
                "receive_account_id": null,
                "receive_cancellation_account_id": null,
                "receive_cancellation_on": null,
                "fulfillment_line_items": [
                    {
                        "id": 33444599,
                        "created_on": "2018-07-02T04:36:03Z",
                        "modified_on": "2018-07-02T04:36:03Z",
                        "order_line_item_id": 23651451,
                        "product_id": 3262674,
                        "product_name": "Quần vải ống suông Farah",
                        "variant_id": 4653234,
                        "variant_name": "Quần vải ống suông Farah",
                        "order_line_item_note": null,
                        "is_freeform": false,
                        "is_composite": false,
                        "is_packsize": false,
                        "base_price": 1400000,
                        "quantity": 1,
                        "tax_type_id": null,
                        "tax_rate_override": 0,
                        "tax_rate": 0,
                        "line_amount": 1400000,
                        "line_tax_amount": 0,
                        "line_discount_amount": 0,
                        "discount_value": 0,
                        "discount_rate": 0,
                        "variant": null,
                        "sku": "SP2",
                        "barcode": "SP2",
                        "unit": null,
                        "variant_options": "Mặc định"
                    }
                ],
                "shipment": null,
                "payments": [],
                "total_quantity": 1,
                "reason_cancel_id": null
            }
        ],
        "order_returns": [
            {
                "id": 200303,
                "tenant_id": 56322,
                "location_id": 58369,
                "code": "SR0207184",
                "account_id": 72098,
                "order_id": 14900465,
                "order_code": "SO26061820",
                "customer_id": 3281243,
                "billing_address": {
                    "id": 17978082,
                    "label": null,
                    "first_name": "Hoàng Sơn",
                    "last_name": "Nguyễn",
                    "address1": "Tựu Liệt",
                    "address2": null,
                    "email": null,
                    "phone_number": null,
                    "country": "Việt Nam",
                    "city": "Hà Nội",
                    "district": "Huyện Thanh Trì",
                    "zip_code": null,
                    "full_address": null
                },
                "contact_id": null,
                "reference": null,
                "note": null,
                "status": "returned",
                "refund_status": "unpaid",
                "total_amount": 1400000,
                "total_quantity": null,
                "issued_on": "2018-07-02T04:36:11Z",
                "received_on": "2018-07-02T04:38:48Z",
                "created_on": "2018-07-02T04:36:22Z",
                "modified_on": "2018-07-02T04:38:48Z",
                "line_items": [
                    {
                        "id": 375007,
                        "order_line_item_id": 23651451,
                        "product_id": 3262674,
                        "product_name": "Quần vải ống suông Farah",
                        "variant_id": 4653234,
                        "variant_name": "Quần vải ống suông Farah",
                        "note": null,
                        "quantity": 1,
                        "price": 1400000,
                        "is_composite": false,
                        "is_freeform": false,
                        "line_amount": 1400000,
                        "created_on": "2018-07-02T04:36:22Z",
                        "modified_on": "2018-07-02T04:36:22Z",
                        "sku": "SP2",
                        "barcode": "SP2",
                        "unit": null,
                        "variant_options": "Mặc định"
                    }
                ],
                "refunds": [],
                "reason_id": null
            }
        ],
        "business_version": 2,
        "expected_payment_method_id": null,
        "expected_delivery_type": null,
        "expected_delivery_provider_id": null,
        "process_status_id": null,
        "reason_cancel_id": null,
        "finalized_on": "2018-06-26T04:42:21Z",
        "finished_on": null,
        "completed_on": null,
        "channel": null,
        "promotion_redemption_id": null,
        "promotion_name": null,
        "promotion_code": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Đơn hàng không tồn tại"
    }
}
```

# Thanh Toán Trước
## Tạo phiếu thanh toán trước
Khách hàng yêu cầu thanh toán trước tới nhân viên, nhân viên gửi yêu cầu thông qua API cho Sapo.vn yêu cầu tạo phiếu thanh toán trước.
**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------|:-------------|
| Prepayment.payment_method_id | yes | int - Id định danh cho đơn hàng được thanh toán trước |
| Prepayment.amount |	yes | bigdecimal - Tổng khối lượng sản phẩm được thanh toán trước|
| Prepayment.note | no | string - Ghi chú cho đơn hàng được thanh toán trước (nếu có) . Trường này có thể NULL |
| Prepayment.paid_on | yes | date - Thời gian khách hàng đã trả tiền |

```
POST /admin/orders/{id}/prepayments.json HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
{
  "prepayment": {
    "payment_method_id": 3647,
    "amount": 20000,
    "note": "hihi",
    "paid_on": null
  }
}
```
**Kết quả trả về**
```

```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "payment_method": "Phương thức thanh toán không tồn tại"
        }
    }
}
```
## Hủy phiếu thanh toán trước
Trong trường hợp nhân viên đã tạo phiếu thanh toán trước nhưng khách hàng lại không muốn mua hàng thì nhân viên sẽ tiến hành hủy phiếu thanh toán trước.

