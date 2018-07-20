# Nhóm nhà cung cấp

Một tài nguyên Supplier đại diện cho một đơn vị cung cấp sản phẩm cho Shop. Tài khoản Supplier lưu trữ thông tin liên hệ của nhà cung cấp giúp cho chủ shop không phải khai báo thông tin nhà cung cấp mỗi khi tạo đơn hàng. 
 
Chủ shop có thể quản lý nhà cung cấp theo nhóm để tiện áp dụng các phương thức thanh toán, kế hoạch nhập hàng. 
Chú ý: Mỗi nhà cung cấp chỉ có thể nằm trong một nhóm nhà cung cấp.

[1. Tạo nhóm khách hàng](#add-customer_groups)

[2. Cập nhật nhóm khách hàng](#put-customer_groups)

[3. Xóa nhóm khách hàng](#delete-customer_groups)

[4. Lấy 1 nhóm khách hàng theo id](#get-customer_groups_id)

[5. Lấy toàn bộ nhóm khách hàng](#get-customer_groups)

[6. Lấy nhóm khách hàng theo bộ lọc](#get-customer_groups?)

## 1. Tạo mới nhóm nhà cung cấp
Bắt đầu với việc tạo nhóm nhà cung cấp, bạn sẽ đưa ra những tùy chọn nhóm để thêm nhà cung cấp vào danh sách.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------:|:-------------|
| Supplier_group.name | yes | Tên nhóm nhà cung cấp, tên nhóm không được trùng với nhóm đã có trước đó  |
| Supplier_group.is_default |	yes | |
| Supplier_group.code | yes | Mã tham chiếu đến nhóm nhà cung cấp trong hệ thống |
| Supplier_group.note| no | Ghi chú, mô tả cho nhóm nhà cung cấp (nếu có) . Trường này có thể NULL |

**Request**

```
POST/admin/supplier_groups HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json


```

**Kết quả trả về**
```
```
## Cập nhật nhóm nhà cung cấp

Bạn có thể sửa đổi và cập nhật các thuộc tính trong nhóm nhà cung cấp đã được tạo trước đó.

**Các tham số**

| Tham số | Bắt buộc | Mô tả |
| ------------- |:-------------:|:-------------|
| Supplier_group.id |	yes | Id định danh cho nhóm nhà cung cấp trong hệ thống. Trường không bắt buộc người dùng điền, tự sinh dưới hệ thống khi để trống. |
| Supplier_group.tenant_id |	yes | id định danh cho nhân viên thực hiện tạo nhóm nhà cung cấp  |
| Supplier_group.created_on |	yes | Thời gian nhóm nhà cung cấp được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| Supplier_group.modified_on |	yes | Thời gian nhóm nhà cung cấp được chỉnh sửa. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| Supplier_group.name | yes | Tên nhóm nhà cung cấp, tên nhóm không được trùng với nhóm đã có trước đó |
| Supplier_group.name_translate | no | Tên nhóm nhà cung cấp |
| Supplier_group.status |	yes | Trạng thái nhóm nhà cung cấp |
| Supplier_group.is_default | yes |  |
| Supplier_group.code | yes | Mã tham chiếu đến nhóm nhà cung cấp  |
| Supplier_group.note| no | Ghi chú cho nhóm nhà cung cấp (nếu có) . Trường này có thể NULL |
| Supplier_group.count_supplier | yes | Mã tham chiếu đến nhóm nhà cung cấp trong hệ thống |

**[POST/admin/customer_groups/id.json]**
```
PUT/admin/supplier_groups/id.json HTTP/1.1
Host: autotest.mysapo.vn
"{
    ""supplier_group"": {
        ""id"": 14379,
        ""tenant_id"": 9287,
        ""created_on"": ""2017-06-20T02:54:06Z"",
        ""modified_on"": ""2017-06-20T02:55:06Z"",
        ""name"": ""New Sun group1"",
        ""name_translate"": ""New Sun group1"",
        ""status"": ""active"",
        ""is_default"": false,
        ""note"": null,
        ""code"": ""CT200617541"",
        ""count_supplier"": null
    }
}"

```
**Kết quả trả về**
```
```
## Xóa nhóm khách hàng
Khi nhóm khách hàng đã tồn tại trong hệ thống, bạn hoàn toàn có thể thực hiện xóa nhóm khách hàng.
**[DELETE/admin/supplier_groups/id.json]**
```
DELETE/admin/supplier_groups/id.json 
HTTP/1.1 200 OK
{}
```
## Lấy 1 nhóm khách hàng theo id
**[GET/admin/supplier_groups/id.json]**

## Lấy toàn bộ nhóm khách hàng
**[GET/admin/supplier_groups.json]**
