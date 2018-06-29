# Đối tượng Voucher
Đối tượng chứng từ sẽ quản lý tổng quan về sổ quỹ tiền mặt của cửa hàng của các chi nhánh (nếu có), các loại phiếu thu, phiếu chi, sổ quỹ và hạch toán kinh doanh cho cửa hàng.
## Tạo mới đối tượng quản lý Vouchers
**Request**
```
POST /admin/vouchers_actors HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
"{
""voucher_actor"":{
""name"":""Thưởng""
}
}"
```
**Kết quả trả về**
```
"{
  ""voucher_actor"": {
    ""id"": 2,
    ""tenant_id"": 9287,
    ""name"": ""Thưởng"",
    ""created_on"": ""2017-03-10T11:24:08Z"",
    ""modified_on"": ""2017-03-10T11:24:08Z""
  }
}"
```
**Trường hợp xảy ra lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "name": "Tên đối tượng đã tồn tại"
        }
    }
}
```
## Lấy 1 đối tượng vouchers theo id
**Request**
```
GET /admin/vouchers_actors/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
{
    "voucher_actor": {
        "id": 9362,
        "tenant_id": 56322,
        "name": "Sơn",
        "created_on": "2018-06-29T06:46:12Z",
        "modified_on": "2018-06-29T06:46:12Z",
        "status": "active"
    }
}
```
## Lấy toàn bộ danh sách đối tượng vouchers
**Request**
```
GET /admin/vouchers_actors?query= HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
**Kết quả trả về**
```
```
**Trường hợp xảy ra lỗi**
```

```
