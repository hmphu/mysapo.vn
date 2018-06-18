# Webhooks
Một Webhook là một công cụ để truy vấn và lưu trữ dữ liệu của một Event xác định. Bạn có thể đăng ký đường dẫn http:// hoặc https:// - nơi mà dữ liệu của Event được lưu trữ dưới dạng XML hoặc JSON. Webhook có thể được đăng ký cho các Event sau

| Chức năng| Method |
| ------------- |:-------------|
| App	| installed |
| Product |	create/update/delete |
| Order |	create/update/cancelled/delete/active/finalized/invoiced/partial_invoiced/fulfilled/partial_fulfilled/paid/partial_paid |
| Order | Transaction	create |
| Customer | create/delete/update |
| Order Return | create/update/cancelled/returned/partial_refund/refund |
| Inventory |	update |
## Bạn có thể làm gì với Webhooks?
Sapo API cho phép bạn thực hiện các thao tác sau với tài nguyên Product. Các phiên bản chi tiết hơn của những thao tác này có thể có

[GET /admin/webhooks.json]
Lấy danh sách tất cả các Webhook

[GET /admin/webhooks/#{id}.json]
Lấy một Webhook

[POST /admin/webhooks.json]
Tạo mới một Webhook

[PUT /admin/webhooks/#{id}.json]
Cập nhật một Webhook

## Các thuộc tính của Webhooks
|  |  |
| ------------- |:-------------|
| address | { "address" : "http://whatever.hostname.com/" } . Địa chỉ URI mà Webhook sẽ gửi một POST Request đến khi có Event xảy ra. |
| created_on | { "created_on" : "2012-09-28T11:50:07-04:00" } Thời gian Webhook được tạo. API trả về kết quả theo định dạng chuẩn ISO 8601. |
| format | { "format" : "json" } . Định dạng kiểu dữ liệu mà Webhook trả về. Các giá trị hợp lệ là json và xml. |
| id | { "id" : 4759306 } . Số duy nhất định danh Webhook. |
| topic | { "topic" : "orders/create" } . Event mà khi xảy ra sẽ thực hiện lời gọi Webhook. Các giá trị hợp lệ là: products/create, products/delete, products/update, orders/create, orders/update, orders/cancelled, orders/delete, orders/active, orders/finalized, orders/invoiced, orders/partial_invoiced, orders/fulfilled, orders/partial_fulfilled, orders/paid, orders/partial_paid, customers/create, customers/update, customers/delete, suppliers/create, suppliers/update, suppliers/delete, order_returns/create, order_returns/update, order_returns/cancelled, order_returns/returned, order_returns/partial_refund, order_returns/refund, inventories/update |
| modified_on | { "modified_on" : "2012-09-28T11:50:07-04:00" } . Thời gian Webhook được cập nhật. API trả về kết quả theo định dạng chuẩn ISO 8601. |
