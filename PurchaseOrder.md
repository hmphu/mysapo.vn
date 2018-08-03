[1. Nhập hàng](#purchase_orders)

   [1.1 Thêm mới đơn nhập hàng](#add-purchase_orders)

   [1.2 Lấy đơn nhập hàng theo bộ lọc?](#get-purchase_orders?)

   [1.3 Lấy một đơn nhập hàng](#get-purchase_orders_id)

   [1.4 Sinh mã code đơn nhập hàng](#purchase_orders_codes)

   [1.5 Chuyển trạng thái từ draft sang active](#purchase_orders_id_status)

   [1.6 Hủy một đơn nhập](#purchase_orders_id_status)

   [1.7 Cập nhật một đơn nhập hàng](#import_purchase_orders_id)

   [1.8 Thêm mới một item](#import_purchase_orders_id)
   
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

<a name= "get-price_adjustments"></a>
# 1. Nhập hàng 
<a name= "get-price_adjustments"></a>
## 1.  Lấy tất cả phiếu điều chỉnh giá vốn
**Request**

```
GET admin/price_adjustments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "metadata": {
        "total": 2,
        "page": 1,
        "limit": 10
    },
    "price_adjustments": [
        {
            "id": 6028,
            "tenant_id": 21406,
            "location_id": 22322,
            "account_id": 25153,
            "created_on": "2018-08-03T07:55:42Z",
            "modified_on": "2018-08-03T07:55:47Z",
            "adjusted_on": "2018-08-03T07:55:47Z",
            "status": "adjusted",
            "code": "CA0308181",
            "note": null,
            "tags": "",
            "total": 2,
            "line_items": [
                {
                    "id": 365156,
                    "price_adjustment_id": 6028,
                    "product_id": 1777552,
                    "variant_id": 2441207,
                    "created_on": "2018-08-03T07:55:42Z",
                    "modified_on": "2018-08-03T07:55:42Z",
                    "note": null,
                    "price": 80,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 365157,
                    "price_adjustment_id": 6028,
                    "product_id": 1015973,
                    "variant_id": 1376284,
                    "created_on": "2018-08-03T07:55:42Z",
                    "modified_on": "2018-08-03T07:55:42Z",
                    "note": null,
                    "price": 150000,
                    "adjusted_price": null,
                    "previous_price": null
                }
            ]
        },
        {
            "id": 1588,
            "tenant_id": 21406,
            "location_id": 22322,
            "account_id": 25153,
            "created_on": "2017-10-14T02:33:27Z",
            "modified_on": "2017-10-14T02:33:27Z",
            "adjusted_on": null,
            "status": "active",
            "code": "CA001",
            "note": null,
            "tags": "",
            "total": 9,
            "line_items": [
                {
                    "id": 85397,
                    "price_adjustment_id": 1588,
                    "product_id": 1015969,
                    "variant_id": 1376280,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85398,
                    "price_adjustment_id": 1588,
                    "product_id": 1015968,
                    "variant_id": 1376279,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85399,
                    "price_adjustment_id": 1588,
                    "product_id": 1015967,
                    "variant_id": 1376278,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85400,
                    "price_adjustment_id": 1588,
                    "product_id": 1015966,
                    "variant_id": 1376277,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85401,
                    "price_adjustment_id": 1588,
                    "product_id": 1015965,
                    "variant_id": 1376276,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85402,
                    "price_adjustment_id": 1588,
                    "product_id": 1015964,
                    "variant_id": 1376275,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85403,
                    "price_adjustment_id": 1588,
                    "product_id": 1015963,
                    "variant_id": 1376274,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85404,
                    "price_adjustment_id": 1588,
                    "product_id": 1015515,
                    "variant_id": 1375790,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                },
                {
                    "id": 85405,
                    "price_adjustment_id": 1588,
                    "product_id": 998156,
                    "variant_id": 1353127,
                    "created_on": "2017-10-14T02:33:27Z",
                    "modified_on": "2017-10-14T02:33:27Z",
                    "note": null,
                    "price": 10,
                    "adjusted_price": null,
                    "previous_price": null
                }
            ]
        }
    ]
}
```
<a name= "get-price_adjustments_id"></a>
## 2. Lấy một phiếu điều chỉnh giá vốn 

**Request**
```
GET Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```

<a name= "get-price_adjustments_codes"></a>
## 3.  Lấy mã code phiếu điều chỉnh giá vốn

**Request**
```
GET admin/price_adjustments/codes HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```

```
<a name= "put-price_adjustments_id"></a>
## 4. Cập nhật một phiếu điều chỉnh giá vốn
**Request**
```
PUT admin/price_adjustments/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "stock_transfer": {
        "code": "ST3007181",
        "tenant_id": 21406
    }
}
```
<a name="add-price_adjustments"></a>
## 5. Thêm một phiếu điều chỉnh giá vốn

**Request**
```
POST admin/price_adjustments HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

params: statuses = draft
```
**Kết quả trả về**
```

```
<a name="price_adjustments_id_status"></a>
## 6. Thay đổi trạng thái của phiếu điều chỉnh giá vốn

**Request**
```
POST admin/price_adjustments/{id}/{status} HTTP/1.1
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

<a name="import_price_adjustments_id"></a>
## 7. Xuất một phiếu điều chỉnh giá vốn

**Request**
```
POST admin/price_adjustments/import HTTP/1.1 
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
