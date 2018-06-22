# Nhóm khách hàng

Một tài nguyên Customer đại diện cho một tài khoản khách hàng của Shop. Tài khoản Customer lưu trữ thông tin liên hệ của khách hàng giúp cho người dùng đã đăng nhập không phải khai báo thông tin mỗi khi thực hiện đặt hàng. 
Vì lí do bảo mật, tài nguyên Customer trên Sapo.vn không lưu thông tin thẻ của khách hàng. Khách hàng sẽ vẫn phải cung cấp thông tin thẻ mỗi khi thực hiện thanh toán.

Người dùng có thể quản lý khách hàng theo nhóm để tiện áp dụng cho các chương trình ưu đãi cũng như khuyến mại của cửa hàng. 
Chú ý: Mỗi khách hàng chỉ có thể nằm trong một nhóm khách hàng.
## Tạo nhóm khách hàng
Bắt đầu với việc tạo nhóm khách hàng, bạn sẽ đưa ra những tùy chọn nhóm để thêm khách hàng vào danh sách.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------:|:-------------|
| Customer_group.name | yes | Tên nhóm khách hàng, tên nhóm không được trùng với nhóm đã có trước đó  |
| Customer_group.is_default |	yes | |
| Customer_group.default_payment_term_id | yes |  |
| Customer_group.default_payment_method_id | yes | Id định danh phương thức thanh toán |
| Customer_group.default_tax_type_id"":  | yes | Id định danh mã số thuế |
| Customer_group.default_discount_rate | yes | Tỷ lệ phần trăm giảm giá được quy định nhóm khách hàng |
| Customer_group.default_price_list_id |	yes | Id định danh danh sách hàng  |
| Customer_group.code | yes | Mã tham chiếu đến nhóm khách hàng trong hệ thống |
| Customer_group.note|	no | Ghi chú cho nhóm khách hàng (nếu có) . Trường này có thể NULL |

**[POST/admin/customer_groups.json]**

`POST/admin/customer_groups.json HTTP/1.1
Host: autotest.mysapo.vn
"{
    ""customer_group"": {
        ""name"": ""New Sun group1"",
        ""is_default"": false,
        ""default_payment_term_id"": 0,
        ""default_payment_method_id"": 0,
        ""default_tax_type_id"": 0,
        ""default_discount_rate"": 0,
        ""default_price_list_id"": 0,
        ""note"": null,
        ""code"": ""CT200617541""
    }
}"`

**Kết quả trả về**
```
```
## Cập nhật nhóm khách hàng

Bạn có thể sửa đổi và cập nhật các thuộc tính trong nhóm khách hàng đã được tạo trước đó.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------:|:-------------|
| Customer_group.id |	yes | Id định danh cho nhóm khách hàng trong hệ thống. Trường không bắt buộc người dùng điền, tự sinh dưới hệ thống khi để trống. |
| Customer_group.tenant_id |	yes | id định danh cho nhân viên thực hiện tạo nhóm khách hàng  |
| Customer_group.created_on |	yes | Thời gian nhóm khách hàng được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| Customer_group.modified_on |	yes | Thời gian nhóm khách hàng được chỉnh sửa. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| Customer_group.name | yes | Tên nhóm khách hàng, tên nhóm không được trùng với nhóm đã có trước đó |
| Customer_group.name_translate | no | Tên nhóm khách hàng |
| Customer_group.status |	yes | Trạng thái nhóm khách hàng |
| Customer_group.is_default | yes |  |
| Customer_group.default_payment_term_id | yes | id định danh cho kỳ hạn thanh toán |
| Customer_group.default_payment_method_id | yes | Id định danh phương thức thanh toán |
| Customer_group.default_tax_type_id"":  | yes | Id định danh mã số thuế |
| Customer_group.default_discount_rate | yes | Tỷ lệ phần trăm giảm giá được quy định nhóm khách hàng |
| Customer_group.default_price_list_id |	yes | Id định danh danh sách hàng  |
| Customer_group.code | yes | Mã tham chiếu đến nhóm khách hàng |
| Customer_group.note|	no | Ghi chú cho nhóm khách hàng (nếu có) . Trường này có thể NULL |
| Customer_group.count_customer | yes | Mã tham chiếu đến nhóm khách hàng trong hệ thống |

**[POST/admin/customer_groups/id.json]**
```
PUT/admin/customer_groups/id.json HTTP/1.1
Host: autotest.mysapo.vn
"{
    ""customer_group"": {
        ""id"": 14379,
        ""tenant_id"": 9287,
        ""created_on"": ""2017-06-20T02:54:06Z"",
        ""modified_on"": ""2017-06-20T02:55:06Z"",
        ""name"": ""New Sun group1"",
        ""name_translate"": ""New Sun group1"",
        ""status"": ""active"",
        ""is_default"": false,
        ""default_payment_term_id"": 0,
        ""default_payment_method_id"": 0,
        ""default_tax_type_id"": 0,
        ""default_discount_rate"": 0,
        ""default_price_list_id"": 0,
        ""note"": null,
        ""code"": ""CT200617541"",
        ""count_customer"": null
    }
}"

```
**Kết quả trả về**
```
```
## Xóa nhóm khách hàng
Khi nhóm khách hàng đã tồn tại trong hệ thống, bạn hoàn toàn có thể thực hiện xóa nhóm khách hàng.
**[DELETE/admin/customer_groups/id.json]**
```
DELETE/admin/customer_groups/id.json 
HTTP/1.1 200 OK
{}

## Lấy 1 nhóm khách hàng theo id
**[GET/admin/customer_groups/id.json]**

