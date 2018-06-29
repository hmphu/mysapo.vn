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

POST /admin/vouchers_actors HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{"order_return":{"id":1635,"tenant_id":77,"location_id":81,"code":"SR1810161","account_id":33,"order_id":7859,"order_code":null,"customer_id":10080,"billing_address":null,"contact_id":null,"reference":null,"note":null,"status":"returning","refund_status":"partial","total_amount":10000,"issued_on":"2016-10-18T08:54:16Z","received_on":null,"created_on":"2016-10-18T08:54:16Z","modified_on":"2016-10-18T08:54:43Z","line_items":[{"id":2074,"product_id":27970,"product_name":"Hoa lay ơn trắng","variant_id":34198,"variant_name":"Hoa lay ơn trắng","note":null,"quantity":1,"price":10000,"is_composite":false,"is_freeform":false,"line_amount":10000,"created_on":"2016-10-18T08:54:16Z","modified_on":"2016-10-18T08:54:16Z"}]}}
