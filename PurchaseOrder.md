[1. Nhập hàng](#purchase_orders)

   [1.1 Thêm mới đơn nhập hàng](#add-purchase_orders)

   [1.2 Lấy đơn nhập hàng theo bộ lọc?](#get-purchase_orders?)

   [1.3 Lấy một đơn nhập hàng](#get-purchase_orders_id)

   [1.4 Sinh mã code đơn nhập hàng](#purchase_orders_codes)

   [1.5 Chuyển trạng thái từ draft sang active](#purchase_orders_id_status)

   [1.6 Hủy một đơn nhập](#cancel-purchase_orders_id_status)

   [1.7 Cập nhật một đơn nhập hàng](#put-purchase_orders_id)

   [1.8 Thêm mới một item](#put-purchase_orders_id_line_items)
   
[2. Hóa đơn nhập](#purchase_orders_bill)

   [2.1 Thêm mới 1 hoá đơn nhập hàng](#add-purchase_orders_bill)

   [2.2 Lấy ra thông tin bill](#get-purchase_orders_bill_id)

   [2.3 Cập nhật thông tin](#put-purchase_orders_bill_id)

   [2.4 Hủy 1 phiếu bill](#cancel-purchase_orders_bill_id)

   [2.5 Lấy bill theo fillter](#get-purchase_orders_bill?)
   
[3. Thanh toán cho hóa đơn nhập](#purchase_orders_bill_payment)

   [3.1 Thêm mới một phiếu thanh toán cho hóa đơn nhập](#get-purchase_orders_bill_payment)

   [3.2 Lấy một phiếu thanh toán hóa đơn nhập](#get-purchase_orders_bill_payment_id)

   [3.3 Hủy phiếu thanh toán](#cancel-purchase_orders_bill_payments)
   
[4. Nhập kho](#purchase_orders_procurements)

   [4.1 Thêm mới phiếu nhập kho](#add-purchase_orders_id_procurements)

   [4.2 Cập nhật một phiếu nhập kho](#get-purchase_orders_id_procurements)

   [4.3 Hủy 1 phiếu nhập kho](#cancel-purchase_orders_id_procurements)

   [4.4 Lấy phiếu nhập kho theo bộ lọc](#get-purchase_orders_id_procurements?)
   
 [5. Trả hàng](#purchase_order_returns) 

   [5.1 Thêm mới một đơn trả hàng](#add-purchase_order_returns)  

**Các tham số**

<a name= "purchase_orders"></a>
# 1. Nhập hàng 

<a name= "add-purchase_orders"></a>
## 1.1 Thêm mới đơn nhập hàng]

**Request**

```
POST /admin/purchase_orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "get-purchase_orders?"></a>
## 1.2 Lấy đơn nhập hàng theo bộ lọc

**Request**
```
GET /admin/purchase_orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```

<a name= "get-purchase_orders_id"></a>
## 1.3 Lấy một đơn nhập hàng

**Request**
```
GET /admin/purchase_orders/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "purchase_orders_codes"></a>
## 1.4 Sinh mã code đơn nhập hàng
**Request**
```
POST /admin/purchase_orders/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name="purchase_orders_id_status"></a>
## 1.5 Chuyển trạng thái từ draft sang active
**Request**
```
POST admin/purchase_orders/{id}/{status} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

params: statuses = draft
```
**Kết quả trả về**
```

```
<a name="cancel-purchase_orders_id"></a>
## 1.6 Hủy một đơn nhập

**Request**
```
POST admin/purchase_orders/{id}/cancel HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
```
**Trường hợp có lỗi**
```

```

<a name="put-purchase_orders_id"></a>
## 1.7 Cập nhật một đơn nhập hàng

**Request**
```
PUT admin/purchase_orders/id HTTP/1.1 
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
Status 200 OK
```
**Trường hợp có lỗi**
```

```
<a name="add-purchase_orders_id_line_items"></a>
## 1.8 Thêm mới một item

**Request**
```
POST /admin/purchase_orders/{id}/line_items HTTP/1.1 
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
Status 200 OK
```
**Trường hợp có lỗi**
```

```
# 2. Nhập hàng 

<a name= "add-purchase_orders"></a>
## 1.1 Thêm mới đơn nhập hàng]

**Request**

```
POST /admin/purchase_orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "get-purchase_orders?"></a>
## 1.2 Lấy đơn nhập hàng theo bộ lọc

**Request**
```
GET /admin/purchase_orders HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```

<a name= "get-purchase_orders_id"></a>
## 1.3 Lấy một đơn nhập hàng

**Request**
```
GET /admin/purchase_orders/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "purchase_orders_codes"></a>
## 1.4 Sinh mã code đơn nhập hàng
**Request**
```
POST /admin/purchase_orders/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name="purchase_orders_id_status"></a>
## 1.5 Chuyển trạng thái từ draft sang active
**Request**
```
POST admin/purchase_orders/{id}/{status} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

params: statuses = draft
```
**Kết quả trả về**
```

```
