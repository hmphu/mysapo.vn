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
## Lấy 1 đối tượng vouchers theo id
```
GET /admin/vouchers_actors/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```
## Lấy toàn bộ danh sách đối tượng vouchers
```
GET /admin/vouchers_actors?query HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
```

