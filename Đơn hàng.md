# Đơn hàng
[1. Order](#order)

   [ 1.1 Đăng đơn hàng mới](#order)

   [ 1.2 Duyệt đơn hàng](#finalize)

   [ 1.3 Hủy đơn hàng](#cancel)

   [ 1.4 Hoàn thành đơn hàng](#finish)

   [ 1.5 Cập nhật đơn hàng](#put-order)

   [ 1.6 Lấy danh sách đơn hàng](#get-order)

   [ 1.7 Lấy danh sách đơn hàng theo id](#get-by-orderid)
   
[2. Thanh Toán Trước](#prepayment)

   [ 2.1 Tạo phiếu thanh toán trước](#add-prepayments)
    
   [ 2.2 Hủy phiếu thanh toán trước](#prepayments-cancel)
    
[3. Đóng gói](#fulfillment)

   [ 3.1 Thêm một đơn hàng được đóng gói](#add-fulfillments)
    
   [ 3.2 Thêm một đơn xuất kho gói hàng](#add-fulfillments-ship)
    
   [ 3.3 Chuyển gói hàng sang trạng thái đã nhận](#fulfillments-receive)
    
   [ 3.4 Hủy gói hàng](#fulfillments-cancel)
    
   [ 3.5 Nhận gói hàng về kho sau khi hủy](#fulfillments-receive_after_cancellation)
   
   [ 3.6 Lấy danh sách đơn hàng được đóng gói](#get-fulfillments)
    
   [ 3.7 Cập nhật đơn hàng được đóng gói](#put-fulfillments)
    
[4. In](#print)

   [ 4.1 lấy mẫu in đóng gói](#get-fulfillment-print-forms)
   
   [ 4.2 lấy mẫu in giao hàng](#get-shipment-print-forms)
   
   [ 4.3 lấy mẫu in đóng gói](#get-order-print-forms)
   
[5.Shipper](#Shipper)

   [ 5.1 Chi tiết Shipper](#delivery-service-providers)
   
   [ 5.2 Công nợ Shipper](#debt-change)
   
<a name="order"></a>
## 1. Order

<a name="order"></a>
### 1.1 Đăng đơn hàng mới
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
| Prepayment.payment_method_id | yes | int - Id định danh cho đơn hàng được thanh toán trước |
| Prepayment.amount |	yes | bigdecimal - Tổng khối lượng sản phẩm được thanh toán trước|
| Prepayment.note | no | string - Ghi chú cho đơn hàng được thanh toán trước (nếu có) . Trường này có thể NULL |
| Prepayment.paid_on | yes | date - Thời gian khách hàng đã trả tiền |

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
<a name="finalize"></a>
### 1.2 Duyệt đơn hàng 
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
<a name="cancel"></a>
### 1.3 Hủy đơn hàng
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
<a name="finish"></a>
### 1.4 Hoàn thành đơn hàng
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
<a name="put-order"></a>
### 1.5 Cập nhật đơn hàng
**Request**
```
PUT /admin/orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "order": {
    "id": 15415310,
    "tenant_id": 56322,
    "location_id": 58369,
    "code": "hungcode",
    "created_on": "2018-07-09T08:17:45Z",
    "modified_on": "2018-07-09T08:17:45Z",
    "issued_on": "2018-07-09T08:17:47Z",
    "ship_on": null,
    "ship_on_min": null,
    "ship_on_max": null,
    "account_id": 72098,
    "assignee_id": 83892,
    "customer_id": 3280093,
    "contact_id": null,
    "billing_address": null,
    "shipping_address": null,
    "email": null,
    "phone_number": null,
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
        "id": 24793295,
        "created_on": "2018-07-09T08:17:45Z",
        "modified_on": "2018-07-09T08:17:45Z",
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
**Kết quả trả về khi sửa đơn hàng thành công**
```
{
    "order": {
        "id": 15415310,
        "tenant_id": 56322,
        "location_id": 58369,
        "code": "hungcode",
        "created_on": "2018-07-09T08:17:45Z",
        "modified_on": "2018-07-09T08:21:44Z",
        "issued_on": "2018-07-09T08:17:47Z",
        "ship_on": null,
        "ship_on_min": null,
        "ship_on_max": null,
        "account_id": 72098,
        "assignee_id": 83892,
        "customer_id": 3280093,
        "contact_id": null,
        "billing_address": null,
        "shipping_address": null,
        "email": null,
        "phone_number": null,
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
                "id": 24793295,
                "created_on": "2018-07-09T08:17:45Z",
                "modified_on": "2018-07-09T08:21:44Z",
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

<a name="get-order"></a>
### 1.6 Lấy danh sách đơn hàng
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
<a name="get-by-orderid"></a>
### 1.7 Lấy danh sách 1 đơn hàng theo id
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
<a name="prepayment"></a>
## Thanh toán trước

<a name="add-prepayments"></a>
### 2.1 Tạo phiếu thanh toán trước
Khách hàng yêu cầu thanh toán trước tới nhân viên, nhân viên gửi yêu cầu thông qua API cho Sapo.vn yêu cầu tạo phiếu thanh toán trước.

```
POST /admin/orders/{id}/prepayments.json HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
{
  "prepayment": {
    "payment_method_id": 220256,
    "amount": 20000,
    "note": "hihi",
    "paid_on": null
  }
}
```
**Kết quả trả về**
```
{
    "prepayment": {
        "id": 3471192,
        "payment_method_id": 220256,
        "paid_on": "2018-07-09T05:01:19Z",
        "amount": 20000,
        "account_id": 72098,
        "note": "hihi",
        "created_on": "2018-07-09T05:01:19Z",
        "modified_on": "2018-07-09T05:01:19Z",
        "reference": null,
        "source": "customer_prepaid",
        "paid_amount": 20000,
        "returned_amount": 0,
        "status": "active",
        "integrated": false,
        "status_before_cancelled": null
    }
}
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
<a name="prepayments-cancel"></a>
### 2.2 Hủy phiếu thanh toán trước
Trong trường hợp nhân viên đã tạo phiếu thanh toán trước nhưng khách hàng lại không muốn mua hàng thì nhân viên sẽ tiến hành hủy phiếu thanh toán trước.
```
POST /admin/orders/{order_id}/prepayments/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "prepayment": {
        "id": 3471955,
        "payment_method_id": 220256,
        "paid_on": "2018-07-09T06:58:26Z",
        "amount": 500000,
        "account_id": 72098,
        "note": null,
        "created_on": "2018-07-09T06:58:26Z",
        "modified_on": "2018-07-09T07:00:37Z",
        "reference": null,
        "source": "customer_prepaid",
        "paid_amount": 500000,
        "returned_amount": 0,
        "status": "cancelled",
        "integrated": false,
        "status_before_cancelled": "active"
    }
}
```
**Trường hợp có lỗi 
```
{
    "error": {
        "message": "Không tìm thấy phiếu thanh toán trước"
    }
}
```
<a name="fulfillment"></a>
## 3. Đóng gói (Fulfillment)

Một Fulfillment đại diện cho việc vận chuyển một hay nhiều item của một đơn hàng. Khi một đơn hàng đã được chuyển về trạng thái fulfilled tức là tất cả item trong đơn hàng đã được chuyển đến cho khách hàng.

Rõ ràng, một người chủ Shop luôn muốn chỉ thực hiện một lần giao hàng đối với đơn hàng nhưng đôi khi kích cỡ item hay item có còn trong kho hay không sẽ khiến cho việc giao hàng phải thực hiện nhiều lần. Đó là lí do một đơn hàng có thể có nhiều Fulfillment.

<a name="add-fulfillments"></a>
### 3.1 Thêm một đơn hàng được đóng gói
**Request**
```
POST /admin/orders/{id}/fulfillments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
{
  "fulfillment": {
    "delivery_type": "pickup",
    "fulfillment_line_items": [
      {
        "order_line_item_id": 24792429,
        "quantity": 0.1
      }
    ],
    "billing_address": {
      "address1": "Xóm 3 xã Hải Toàn"
    },
    "shipment": {
      "delivery_service_provider_id": 10355,
      "delivery_fee": 0,
      "cod_amount": 0,
      "freight_amount": 0,
      "detail": "{\"source_location_id\":58369,\"destination_country_id\":201,\"destination_province_id\":1,\"destination_district_id\":2,\"destination_address\":\"sd\",\"delivery_fee\":0.0,\"cod_amount\":800000.0,\"note\":null,\"delivery_service_provider_id\":10355,\"receiver_name\":\"Khách lẻ\",\"receiver_phone\":\"08767465353453\",\"destination_country\":\"Việt Nam\",\"destination_province\":\"Hà Nội\",\"destination_district\":\"Quận Ba Đình\"}"
    }
  }
}
```
**Kết quả trả về**
```
{
    "fulfillment": {
        "id": 34122379,
        "tenant_id": 56322,
        "stock_location_id": 58369,
        "code": "FU0907187",
        "order_id": 15414945,
        "account_id": 72098,
        "assignee_id": 72098,
        "partner_id": 3280093,
        "billing_address": {
            "id": 18328217,
            "label": null,
            "first_name": null,
            "last_name": null,
            "address1": "Xóm 3 xã Hải Toàn",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": null,
            "city": null,
            "district": null,
            "zip_code": null,
            "full_address": null
        },
        "delivery_type": "pickup",
        "tax_treatment": "exclusive",
        "discount_rate": 0,
        "discount_value": 0,
        "discount_amount": 0,
        "total": 80000,
        "total_tax": 0,
        "total_discount": 0,
        "notes": null,
        "packed_on": "2018-07-09T08:27:48Z",
        "received_on": null,
        "shipped_on": null,
        "cancel_date": null,
        "cancel_account_id": null,
        "created_on": "2018-07-09T08:27:48Z",
        "modified_on": "2018-07-09T08:27:48Z",
        "status": "packed",
        "composite_fulfillment_status": null,
        "payment_status": "unpaid",
        "stock_out_account_id": null,
        "receive_account_id": null,
        "receive_cancellation_account_id": null,
        "receive_cancellation_on": null,
        "fulfillment_line_items": [
            {
                "id": 34122378,
                "created_on": "2018-07-09T08:27:48Z",
                "modified_on": "2018-07-09T08:27:48Z",
                "order_line_item_id": 24792429,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_id": 4697237,
                "variant_name": "Áo khoác có mũ Bellfield",
                "order_line_item_note": null,
                "is_freeform": false,
                "is_composite": false,
                "is_packsize": false,
                "base_price": 800000,
                "quantity": 0.1,
                "tax_type_id": null,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "line_amount": 80000,
                "line_tax_amount": 0,
                "line_discount_amount": 0,
                "discount_value": 0,
                "discount_rate": 0,
                "variant": null,
                "sku": "SP10",
                "barcode": "SP10",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "shipment": null,
        "payments": [],
        "total_quantity": 0.1,
        "reason_cancel_id": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Đối tác vận chuyển không tồn tại hoặc không khả dụng"
    }
}
```
<a name="add-fulfillments-ship"></a>
### 3.2 Thêm một đơn xuất kho gói hàng
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{id}/ship HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "order": {
    "id": 15608248,
    "tenant_id": 56322,
    "location_id": 58369,
    "code": "SO1607182",
    "created_on": "2018-07-16T03:44:21Z",
    "modified_on": "2018-07-16T03:45:00Z",
    "issued_on": "2018-07-16T03:44:22Z",
    "ship_on": null,
    "ship_on_min": null,
    "ship_on_max": null,
    "account_id": 72098,
    "assignee_id": 72098,
    "customer_id": 4128452,
    "contact_id": null,
    "billing_address": {
      "id": 18610023,
      "label": "Giao hàng",
      "first_name": null,
      "last_name": null,
      "address1": "Hà Nội",
      "address2": null,
      "email": null,
      "phone_number": null,
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Thị xã Sơn Tây",
      "zip_code": null,
      "full_address": null
    },
    "shipping_address": {
      "id": 18610024,
      "label": "Giao hàng",
      "first_name": null,
      "last_name": null,
      "address1": "Hà Nội",
      "address2": null,
      "email": null,
      "phone_number": null,
      "country": "Việt Nam",
      "city": "Hà Nội",
      "district": "Thị xã Sơn Tây",
      "zip_code": null,
      "full_address": null
    },
    "email": null,
    "phone_number": "0987654320",
    "reference_number": null,
    "price_list_id": 167326,
    "tax_treatment": "exclusive",
    "status": "finalized",
    "packed_status": "packed",
    "fulfillment_status": "unshipped",
    "received_status": "unreceived",
    "payment_status": "unpaid",
    "return_status": "unreturned",
    "source_id": 387299,
    "total": 630000,
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
        "id": 25239610,
        "created_on": "2018-07-16T03:44:21Z",
        "modified_on": "2018-07-16T03:44:21Z",
        "variant_id": 4697232,
        "product_id": 3262678,
        "product_name": "Khăn ống Tommy Hilfiger",
        "variant_name": "Khăn ống Tommy Hilfiger",
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
        "price": 630000,
        "quantity": 1,
        "is_freeform": false,
        "is_composite": false,
        "line_amount": 630000,
        "discount_items": [
          {
            "source": "manual",
            "rate": 0,
            "value": 0,
            "amount": 0,
            "reason": null
          }
        ],
        "sku": "SP7",
        "barcode": "SP7",
        "unit": null,
        "variant_options": "(combo)"
      }
    ],
    "prepayments": [],
    "fulfillments": [
      {
        "id": 34734415,
        "tenant_id": 56322,
        "stock_location_id": 58369,
        "code": "FU1607182",
        "order_id": 15608248,
        "account_id": 72098,
        "assignee_id": 72098,
        "partner_id": 4128452,
        "billing_address": {
          "id": 18610068,
          "label": "Giao hàng",
          "first_name": null,
          "last_name": null,
          "address1": "Hà Nội",
          "address2": null,
          "email": null,
          "phone_number": null,
          "country": "Việt Nam",
          "city": "Hà Nội",
          "district": "Thị xã Sơn Tây",
          "zip_code": null,
          "full_address": null
        },
        "delivery_type": "courier",
        "tax_treatment": "exclusive",
        "discount_rate": 0,
        "discount_value": 0,
        "discount_amount": 0,
        "total": 630000,
        "total_tax": 0,
        "total_discount": 0,
        "notes": null,
        "packed_on": "2018-07-16T03:45:00Z",
        "received_on": null,
        "shipped_on": null,
        "cancel_date": null,
        "cancel_account_id": null,
        "created_on": "2018-07-16T03:45:00Z",
        "modified_on": "2018-07-16T03:45:00Z",
        "status": "packed",
        "composite_fulfillment_status": "packed",
        "payment_status": "unpaid",
        "stock_out_account_id": null,
        "receive_account_id": null,
        "receive_cancellation_account_id": null,
        "receive_cancellation_on": null,
        "fulfillment_line_items": [
          {
            "id": 34734414,
            "created_on": "2018-07-16T03:45:00Z",
            "modified_on": "2018-07-16T03:45:00Z",
            "order_line_item_id": 25239610,
            "product_id": 3262678,
            "product_name": "Khăn ống Tommy Hilfiger",
            "variant_id": 4697232,
            "variant_name": "Khăn ống Tommy Hilfiger",
            "order_line_item_note": null,
            "is_freeform": false,
            "is_composite": false,
            "is_packsize": false,
            "base_price": 630000,
            "quantity": 1,
            "tax_type_id": null,
            "tax_rate_override": 0,
            "tax_rate": 0,
            "line_amount": 630000,
            "line_tax_amount": 0,
            "line_discount_amount": 0,
            "discount_value": 0,
            "discount_rate": 0,
            "variant": null,
            "sku": "SP7",
            "barcode": "SP7",
            "unit": null,
            "variant_options": "(combo)"
          }
        ],
        "shipment": {
          "delivery_service_provider_id": 8342,
          "service_name": null,
          "cod_amount": 630000,
          "freight_amount": 0,
          "freight_amount_detail": null,
          "delivery_fee": 0,
          "tracking_code": "FU1607182",
          "tracking_url": null,
          "created_on": "2018-07-16T03:45:00Z",
          "modified_on": "2018-07-16T03:45:00Z",
          "sender_address": null,
          "shipping_address": {
            "id": 18610069,
            "label": null,
            "first_name": "test 1",
            "last_name": null,
            "address1": "Hà Nội",
            "address2": null,
            "email": null,
            "phone_number": "0987654320",
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Thị xã Sơn Tây",
            "zip_code": null,
            "full_address": null
          },
          "shipper_deposits": [],
          "detail": "{\"source_location_id\":58369,\"destination_country_id\":201,\"destination_province_id\":1,\"destination_district_id\":1,\"destination_address\":\"Hà Nội\",\"delivery_fee\":0.0,\"cod_amount\":630000.0,\"note\":null,\"delivery_service_provider_id\":8342,\"receiver_name\":\"test 1\",\"receiver_phone\":\"0987654320\",\"destination_country\":\"Việt Nam\",\"destination_province\":\"Hà Nội\",\"destination_district\":\"Thị xã Sơn Tây\"}",
          "note": null,
          "pushing_status": null,
          "reference_status": null,
          "reference_status_explanation": null,
          "pushing_note": null,
          "collation_status": "unresolved",
          "delivery_service_provider": null
        },
        "payments": [],
        "total_quantity": 1,
        "reason_cancel_id": null
      }
    ],
    "order_returns": [],
    "business_version": 2,
    "expected_payment_method_id": null,
    "expected_delivery_type": null,
    "expected_delivery_provider_id": null,
    "process_status_id": null,
    "reason_cancel_id": null,
    "finalized_on": "2018-07-16T03:44:21Z",
    "finished_on": null,
    "completed_on": null,
    "channel": null,
    "promotion_redemption_id": null,
    "promotion_name": null,
    "promotion_code": null
  }
}

```
**Kết quả trả về**
```
{
    "fulfillment": {
        "id": 34734415,
        "tenant_id": 56322,
        "stock_location_id": 58369,
        "code": "FU1607182",
        "order_id": 15608248,
        "account_id": 72098,
        "assignee_id": 72098,
        "partner_id": 4128452,
        "billing_address": {
            "id": 18610068,
            "label": "Giao hàng",
            "first_name": null,
            "last_name": null,
            "address1": "Hà Nội",
            "address2": null,
            "email": null,
            "phone_number": null,
            "country": "Việt Nam",
            "city": "Hà Nội",
            "district": "Thị xã Sơn Tây",
            "zip_code": null,
            "full_address": null
        },
        "delivery_type": "courier",
        "tax_treatment": "exclusive",
        "discount_rate": 0,
        "discount_value": 0,
        "discount_amount": 0,
        "total": 630000,
        "total_tax": 0,
        "total_discount": 0,
        "notes": null,
        "packed_on": "2018-07-16T03:45:00Z",
        "received_on": null,
        "shipped_on": "2018-07-16T03:45:43Z",
        "cancel_date": null,
        "cancel_account_id": null,
        "created_on": "2018-07-16T03:45:00Z",
        "modified_on": "2018-07-16T03:45:43Z",
        "status": "fulfilled",
        "composite_fulfillment_status": null,
        "payment_status": "unpaid",
        "stock_out_account_id": 72098,
        "receive_account_id": null,
        "receive_cancellation_account_id": null,
        "receive_cancellation_on": null,
        "fulfillment_line_items": [
            {
                "id": 34734414,
                "created_on": "2018-07-16T03:45:00Z",
                "modified_on": "2018-07-16T03:45:00Z",
                "order_line_item_id": 25239610,
                "product_id": 3262678,
                "product_name": "Khăn ống Tommy Hilfiger",
                "variant_id": 4697232,
                "variant_name": "Khăn ống Tommy Hilfiger",
                "order_line_item_note": null,
                "is_freeform": false,
                "is_composite": false,
                "is_packsize": false,
                "base_price": 630000,
                "quantity": 1,
                "tax_type_id": null,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "line_amount": 630000,
                "line_tax_amount": 0,
                "line_discount_amount": 0,
                "discount_value": 0,
                "discount_rate": 0,
                "variant": null,
                "sku": "SP7",
                "barcode": "SP7",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "shipment": {
            "delivery_service_provider_id": 8342,
            "service_name": null,
            "cod_amount": 630000,
            "freight_amount": 0,
            "freight_amount_detail": null,
            "delivery_fee": 0,
            "tracking_code": "FU1607182",
            "tracking_url": null,
            "created_on": "2018-07-16T03:45:00Z",
            "modified_on": "2018-07-16T03:45:00Z",
            "sender_address": null,
            "shipping_address": {
                "id": 18610069,
                "label": null,
                "first_name": "test 1",
                "last_name": null,
                "address1": "Hà Nội",
                "address2": null,
                "email": null,
                "phone_number": "0987654320",
                "country": "Việt Nam",
                "city": "Hà Nội",
                "district": "Thị xã Sơn Tây",
                "zip_code": null,
                "full_address": null
            },
            "shipper_deposits": [],
            "detail": "{\"source_location_id\":58369,\"destination_country_id\":201,\"destination_province_id\":1,\"destination_district_id\":1,\"destination_address\":\"Hà Nội\",\"delivery_fee\":0.0,\"cod_amount\":630000.0,\"note\":null,\"delivery_service_provider_id\":8342,\"receiver_name\":\"test 1\",\"receiver_phone\":\"0987654320\",\"destination_country\":\"Việt Nam\",\"destination_province\":\"Hà Nội\",\"destination_district\":\"Thị xã Sơn Tây\"}",
            "note": null,
            "pushing_status": null,
            "reference_status": null,
            "reference_status_explanation": null,
            "pushing_note": null,
            "collation_status": "unresolved",
            "delivery_service_provider": null
        },
        "payments": [],
        "total_quantity": 1,
        "reason_cancel_id": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Gói hàng có phương thức giao hàng khác 'Dịch vụ giao hàng', không thể tạo phiếu đặt cọc"
    }
}
```
<a name="fulfillments-receive"></a>
### 3.3 Chuyển gói hàng sang trạng thái đã nhận
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{id}/receive HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "fulfillment": {
        "id": 34120348,
        "tenant_id": 56322,
        "stock_location_id": 58369,
        "code": "FU0907185",
        "order_id": 15414945,
        "account_id": 72098,
        "assignee_id": 72098,
        "partner_id": 3280093,
        "billing_address": null,
        "delivery_type": "courier",
        "tax_treatment": "exclusive",
        "discount_rate": 0,
        "discount_value": 0,
        "discount_amount": 0,
        "total": 80000,
        "total_tax": 0,
        "total_discount": 0,
        "notes": null,
        "packed_on": "2018-07-09T08:11:44Z",
        "received_on": "2018-07-09T09:28:50Z",
        "shipped_on": "2018-07-09T09:16:20Z",
        "cancel_date": null,
        "cancel_account_id": null,
        "created_on": "2018-07-09T08:12:42Z",
        "modified_on": "2018-07-09T09:28:50Z",
        "status": "received",
        "composite_fulfillment_status": null,
        "payment_status": "paid",
        "stock_out_account_id": 72098,
        "receive_account_id": 72098,
        "receive_cancellation_account_id": null,
        "receive_cancellation_on": null,
        "fulfillment_line_items": [
            {
                "id": 34120347,
                "created_on": "2018-07-09T08:12:41Z",
                "modified_on": "2018-07-09T08:12:41Z",
                "order_line_item_id": 24792429,
                "product_id": 3262676,
                "product_name": "Áo khoác có mũ Bellfield",
                "variant_id": 4697237,
                "variant_name": "Áo khoác có mũ Bellfield",
                "order_line_item_note": null,
                "is_freeform": false,
                "is_composite": false,
                "is_packsize": false,
                "base_price": 800000,
                "quantity": 0.1,
                "tax_type_id": null,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "line_amount": 80000,
                "line_tax_amount": 0,
                "line_discount_amount": 0,
                "discount_value": 0,
                "discount_rate": 0,
                "variant": null,
                "sku": "SP10",
                "barcode": "SP10",
                "unit": null,
                "variant_options": "(combo)"
            }
        ],
        "shipment": {
            "delivery_service_provider_id": 10355,
            "service_name": null,
            "cod_amount": 800000,
            "freight_amount": 0,
            "freight_amount_detail": null,
            "delivery_fee": 0,
            "tracking_code": "FU0907185",
            "tracking_url": null,
            "created_on": "2018-07-09T08:12:41Z",
            "modified_on": "2018-07-09T09:16:20Z",
            "sender_address": null,
            "shipping_address": {
                "id": 18327069,
                "label": null,
                "first_name": "Khách lẻ",
                "last_name": null,
                "address1": "sd",
                "address2": null,
                "email": null,
                "phone_number": "08767465353453",
                "country": "Việt Nam",
                "city": "Hà Nội",
                "district": "Quận Ba Đình",
                "zip_code": null,
                "full_address": null
            },
            "shipper_deposits": [
                {
                    "id": 83445,
                    "payment_method_id": 220256,
                    "paid_on": "2018-07-09T09:16:20Z",
                    "amount": 800000,
                    "account_id": 72098,
                    "created_on": "2018-07-09T09:16:20Z",
                    "modified_on": "2018-07-09T09:16:20Z",
                    "status": "active"
                }
            ],
            "detail": "{\"source_location_id\":58369,\"destination_country_id\":201,\"destination_province_id\":1,\"destination_district_id\":2,\"destination_address\":\"sd\",\"delivery_fee\":0.0,\"cod_amount\":800000.0,\"note\":null,\"delivery_service_provider_id\":10355,\"receiver_name\":\"Khách lẻ\",\"receiver_phone\":\"08767465353453\",\"destination_country\":\"Việt Nam\",\"destination_province\":\"Hà Nội\",\"destination_district\":\"Quận Ba Đình\"}",
            "note": null,
            "pushing_status": null,
            "reference_status": null,
            "reference_status_explanation": null,
            "pushing_note": null,
            "collation_status": "unresolved",
            "delivery_service_provider": null
        },
        "payments": [
            {
                "id": 16336353,
                "account_id": 72098,
                "created_on": "2018-07-09T09:28:50Z",
                "modified_on": "2018-07-09T09:28:50Z",
                "payment_method_id": 220258,
                "amount": 80000,
                "reference": null,
                "paid_on": "2018-07-09T09:28:50Z",
                "status": "active",
                "paid_amount": 0,
                "returned_amount": 0,
                "prepayment_id": 3473857
            }
        ],
        "total_quantity": 0.1,
        "reason_cancel_id": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "": "Trạng thái của gói hàng hiện tại không thể chuyển sang 'Đã nhận'"
        }
    }
}
```
<a name="fulfillments-cancel"></a>
### 3.4 Hủy gói hàng
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "fulfillment": {
        "id": 34133534,
        "tenant_id": 56322,
        "stock_location_id": 58369,
        "code": "FU09071810",
        "order_id": 15033904,
        "account_id": 72098,
        "assignee_id": 72098,
        "partner_id": 3280093,
        "billing_address": null,
        "delivery_type": "pickup",
        "tax_treatment": "exclusive",
        "discount_rate": 0,
        "discount_value": 0,
        "discount_amount": 0,
        "total": 500000,
        "total_tax": 0,
        "total_discount": 0,
        "notes": null,
        "packed_on": "2018-07-09T09:32:15Z",
        "received_on": null,
        "shipped_on": null,
        "cancel_date": "2018-07-09T09:32:49Z",
        "cancel_account_id": 72098,
        "created_on": "2018-07-09T09:32:15Z",
        "modified_on": "2018-07-09T09:32:49Z",
        "status": "cancelled",
        "composite_fulfillment_status": null,
        "payment_status": "unpaid",
        "status_before_cancellation": "packed",
        "stock_out_account_id": null,
        "receive_account_id": null,
        "receive_cancellation_account_id": null,
        "receive_cancellation_on": "2018-07-09T09:32:49Z",
        "fulfillment_line_items": [
            {
                "id": 34133533,
                "created_on": "2018-07-09T09:32:15Z",
                "modified_on": "2018-07-09T09:32:15Z",
                "order_line_item_id": 23945755,
                "product_id": 3217942,
                "product_name": "Váy len nữ",
                "variant_id": 4594856,
                "variant_name": "Váy len nữ",
                "order_line_item_note": null,
                "is_freeform": false,
                "is_composite": false,
                "is_packsize": false,
                "base_price": 500000,
                "quantity": 1,
                "tax_type_id": null,
                "tax_rate_override": 0,
                "tax_rate": 0,
                "line_amount": 500000,
                "line_tax_amount": 0,
                "line_discount_amount": 0,
                "discount_value": 0,
                "discount_rate": 0,
                "variant": null,
                "sku": "V0001",
                "barcode": "V0001",
                "unit": null,
                "variant_options": "Trắng / Len co dãn / Zara"
            }
        ],
        "shipment": null,
        "payments": [],
        "total_quantity": 1,
        "reason_cancel_id": null
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "fulfillment có id = 34120348": "Gói hàng đã giao thành công thì không thể hủy. Nếu muốn hoàn lại, hãy tạo phiếu trả hàng"
        }
    }
}
```
<a name="fulfillments-receive_after_cancellation"></a>
### 3.5 Nhận gói hàng về kho sau khi hủy
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{id}/receive_after_cancellation HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
**Trường hợp có lỗi **
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "status": "Chỉ có thể nhận lại gói hàng ở trạng thái 'đã hủy - chờ nhận lại'"
        }
    }
}
```
<a name="get-fulfillments"></a>
### 3.6 Lấy danh sách đơn hàng được đóng gói
**Request**
```
GET /admin/fulfillments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
 "metadata": {
        "total": 19,
        "page": 1,
        "limit": 250
```
<a name="put-fulfillments"></a>
### 3.7 Cập nhật đơn hàng được đóng gói
**Request**
```
PUT /admin/orders/{order_id}/fulfillments/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
 "metadata": {
        "total": 19,
        "page": 1,
        "limit": 250
```
<a name="print"></a>
## 4.In

<a name="get-fulfillment-print-forms"></a>
### 4.1 Lấy mẫu in đóng gói
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{fulfillment_id}/payments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```

<a name="get-shipment-print-forms"></a>
### 4.2 Lấy mẫu in giao hàng
**Request**
```
PUT /admin/orders/{order_id}/fulfillments/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name="get-order-print-forms"></a>
### 4.3 Lấy mẫu in đóng gói
**Request**
```
PUT /admin/orders/{order_id}/fulfillments/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name="Shipper"></a>
## 5. Shipper

<a name="delivery-service-providers"></a>
### 5.1 Chi tiết Shipper
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{fulfillment_id}/payments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
**Trường hợp có lỗi**
```
```
<a name="debt-change"></a>
### 5.2 Công nợ Shipper
**Request**
```
POST /admin/orders/{order_id}/fulfillments/{fulfillment_id}/payments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
**Trường hợp có lỗi**
```
```
