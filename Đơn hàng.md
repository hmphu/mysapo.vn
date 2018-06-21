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
