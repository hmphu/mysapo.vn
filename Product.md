# 1. Sản phẩm

Product là nơi quản lý danh sách sản phẩm, loại sản phẩm..và tất cả những gì liên quan đến các mặt hàng được bán của chủ shop. Product có thể là thực thể, phần mềm số (ví dụ như phim, nhạc, ebook) hoặc dịch vụ (như thuê dụng cụ, công việc cho thuê). Cách hiểu đơn giản nhaas là: nếu một thứ gì đó được bán trong Shop. Hệ thống Sapo POS quản lý sản phẩm tập trung, dễ dàng quản lý lượng nhập mới, lượng tồn kho.. giúp chủ shop đưa ra những quyết định chính xác trong chiến lược kinh doanh của mình.

[1. Sản phẩm](#product)

   [ 1.1 Tạo sản phẩm mới](#add-products)

   [ 1.2 Tạo sản phẩm có packsize](#add-products_packsize)

   [ 1.3 Lấy sản phẩm theo id](#get-product_id)

   [ 1.4 Cập nhật sản phẩm](#put-product_id)

   [ 1.5 Xóa 1 sản phẩm](#delete-product_id)
   
[2. Thanh Toán Trước](#prepayment)

   [ 2.1 Tạo phiếu thanh toán trước](#add-prepayments)
    
<a name="add-products"></a>
## 1.1 Tạo sản phẩm
**Request**
```
POST /admin/products HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

{
  "product": {
    "category": "B1",
    "category_id": 0,
    "brand": "chung",
    "name": "chung 1",
    "brand_id": 0,
    "supplier_id": null,
    "description": "chung",
    "init_stock": 10,
    "initial_cost_price": 10000,
    "tags": "a,d,b",
    "sku": "a1",
    "barcode": "a1",
    "import_price": 10000,
    "whole_sale_price": 11000,
    "retail_price": 12000,
    "variants": null,
    "options": null
  }
}
```
**Kết quả trả về**
```
{
    "product": {
        "id": 3939079,
        "tenant_id": 56322,
        "created_on": "2018-07-25T06:50:01Z",
        "modified_on": "2018-07-25T06:50:01Z",
        "status": "active",
        "brand_id": 130703,
        "brand": "chung",
        "description": "chung",
        "image_path": null,
        "image_name": null,
        "name": "chung 1",
        "opt1": "Kích thước",
        "opt2": null,
        "opt3": null,
        "category_id": 197231,
        "category": "B1",
        "category_code": "PDG2507184",
        "quantity": 1,
        "tags": "a,b,d",
        "available": null,
        "supplier_ids": [],
        "supplier": null,
        "supplier_id": 0,
        "variant_ids": [
            5702358
        ],
        "variants": [
            {
                "id": 5702358,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:50:01Z",
                "modified_on": "2018-07-25T06:50:01Z",
                "category_id": 197231,
                "brand_id": 130703,
                "product_id": 3939079,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": 10000,
                "retail_price": 12000,
                "init_price": 10000,
                "init_stock": 10,
                "max_online": null,
                "variant_retail_price": 12000,
                "variant_whole_price": 11000,
                "variant_import_price": 10000,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "chung 1",
                "online_ordering": true,
                "opt1": "Mặc định",
                "opt2": null,
                "opt3": null,
                "product_name": "chung 1",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "a1",
                "barcode": "a1",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": null,
                "packsize": false,
                "packsize_quantity": null,
                "packsize_root_id": null,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [
                    {
                        "id": 34123476,
                        "value": 11000,
                        "name": "Giá bán buôn",
                        "price_list_id": 167324,
                        "price_list": {
                            "id": 167324,
                            "tenant_id": 56322,
                            "created_on": "2018-05-08T02:07:57Z",
                            "modified_on": "2018-05-08T02:07:57Z",
                            "code": "BANBUON",
                            "name": "Giá bán buôn",
                            "is_cost": false,
                            "currency_id": 56321,
                            "status": "active",
                            "init": true
                        }
                    },
                    {
                        "id": 34123477,
                        "value": 12000,
                        "name": "Giá bán lẻ",
                        "price_list_id": 167326,
                        "price_list": {
                            "id": 167326,
                            "tenant_id": 56322,
                            "created_on": "2018-05-08T02:07:57Z",
                            "modified_on": "2018-05-08T02:07:57Z",
                            "code": "BANLE",
                            "name": "Giá bán lẻ",
                            "is_cost": false,
                            "currency_id": 56321,
                            "status": "default",
                            "init": true
                        }
                    },
                    {
                        "id": 34123478,
                        "value": 10000,
                        "name": "Giá nhập",
                        "price_list_id": 167325,
                        "price_list": {
                            "id": 167325,
                            "tenant_id": 56322,
                            "created_on": "2018-05-08T02:07:57Z",
                            "modified_on": "2018-05-08T02:07:57Z",
                            "code": "GIANHAP",
                            "name": "Giá nhập",
                            "is_cost": true,
                            "currency_id": 56321,
                            "status": "default",
                            "init": true
                        }
                    }
                ],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702358,
                        "mac": 10000,
                        "amount": 0,
                        "on_hand": 10,
                        "available": 10,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            }
        ],
        "options": [
            {
                "id": 4276727,
                "name": "Kích thước",
                "position": 1
            }
        ]
    }
}
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "phiên bản sản phẩm": "Mã a1 đã trùng "
        }
    }
}
```
<a name="add-products_packsize"></a>
## 1.2 Tạo sản phẩm có packsize
**Request**
```
POST /admin/products HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
{
  "product": {
    "status": "active",
    "name": "sp test unit 01",
    "opt1": "Kích thước",
    "opt2": null,
    "opt3": null,
    "variants": [
      {
        "composite": false,
        "keep_selling": true,
        "init_price": 20000,
        "init_stock": 15,
        "name": "sp test unit 01",
        "online_ordering": true,
        "opt1": "M",
        "opt2": null,
        "opt3": null,
        "status": "active",
        "sellable": true,
        "taxable": true,
        "unit": "gói",
        "online": false,
        "packsizes": [
          {
            "composite": false,
            "keep_selling": true,
            "init_price": 20000,
            "init_stock": 15,
            "name": "sp test unit 01",
            "online_ordering": true,
            "opt1": "M",
            "opt2": null,
            "opt3": null,
            "status": "active",
            "sellable": true,
            "taxable": true,
            "online": false,
            "unit": "thùng bé",
            "packsize_quantity": 6
          },
          {
            "composite": false,
            "keep_selling": true,
            "init_price": 20000,
            "init_stock": 15,
            "name": "sp test unit 01",
            "online_ordering": true,
            "opt1": "M",
            "opt2": null,
            "opt3": null,
            "status": "active",
            "sellable": true,
            "taxable": true,
            "online": false,
            "unit": "thùng to",
            "packsize_quantity": "24"
          }
        ]
      }
    ],
    "options": [
      {
        "id": 63460,
        "name": "Kích thước",
        "position": 1
      }
    ]
  }
}
```
**Kết quả trả về**
```
{
    "product": {
        "id": 3939085,
        "tenant_id": 56322,
        "created_on": "2018-07-25T06:52:17Z",
        "modified_on": "2018-07-25T06:52:17Z",
        "status": "active",
        "brand": null,
        "description": null,
        "image_path": null,
        "image_name": null,
        "name": "sp test unit 01",
        "opt1": "Kích thước",
        "opt2": null,
        "opt3": null,
        "category": null,
        "category_code": null,
        "quantity": 3,
        "tags": null,
        "available": null,
        "supplier_ids": [],
        "supplier": null,
        "supplier_id": 0,
        "variant_ids": [
            5702363,
            5702364,
            5702365
        ],
        "variants": [
            {
                "id": 5702363,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP12",
                "barcode": "SP12",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "gói",
                "packsize": false,
                "packsize_quantity": null,
                "packsize_root_id": null,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702363,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 15,
                        "available": 15,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702364,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP13",
                "barcode": "SP13",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng bé",
                "packsize": true,
                "packsize_quantity": 6,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702364,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 2.5,
                        "available": 2.5,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702365,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP14",
                "barcode": "SP14",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng to",
                "packsize": true,
                "packsize_quantity": 24,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702365,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 0.625,
                        "available": 0.625,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            }
        ],
        "options": [
            {
                "id": 4276732,
                "name": "Kích thước",
                "position": 1
            }
        ]
    }
}
```
<a name="get-product_id"></a>
## 1.3 Lấy sản phẩm theo id
**Request**
```
GET /admin/products/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
{
    "product": {
        "id": 3939085,
        "tenant_id": 56322,
        "created_on": "2018-07-25T06:52:17Z",
        "modified_on": "2018-07-25T06:52:17Z",
        "status": "active",
        "brand": null,
        "description": null,
        "image_path": null,
        "image_name": null,
        "name": "sp test unit 01",
        "opt1": "Kích thước",
        "opt2": null,
        "opt3": null,
        "category": null,
        "category_code": null,
        "quantity": 3,
        "tags": null,
        "available": null,
        "supplier_ids": [],
        "supplier": null,
        "supplier_id": 0,
        "variant_ids": [
            5702363,
            5702364,
            5702365
        ],
        "variants": [
            {
                "id": 5702363,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP12",
                "barcode": "SP12",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "gói",
                "packsize": false,
                "packsize_quantity": null,
                "packsize_root_id": null,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702363,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 15,
                        "available": 15,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702364,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP13",
                "barcode": "SP13",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng bé",
                "packsize": true,
                "packsize_quantity": 6,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702364,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 2.5,
                        "available": 2.5,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702365,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:52:17Z",
                "category_id": null,
                "brand_id": null,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "sp test unit 01",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP14",
                "barcode": "SP14",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng to",
                "packsize": true,
                "packsize_quantity": 24,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702365,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 0.625,
                        "available": 0.625,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            }
        ],
        "options": [
            {
                "id": 4276732,
                "name": "Kích thước",
                "position": 1
            }
        ]
    }
}
```
**Trường hợp có lỗi**
```
{
    "error": {
        "message": "Không tìm thấy đối tượng"
    }
}
```
<a name="put-product_id"></a>
## 1.4 Cập nhật sản phẩm
**Request**
```
PUT admin/products/{id} HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json
{
  "product": {
    "category": null,
    "category_id": null,
    "brand": "Thám tử lừng danh Conan ",
    "name": "Thám tử lừng danh Conan",
    "brand_id": null,
    "supplier_id": null,
    "description": "Truyện trinh thám",
    "init_stock": null,
    "initial_cost_price": null,
    "tags": "tags1",
    "sku": "Chung1",
    "status": "active",
    "barcode": "Co1",
    "import_price": 10000,
    "whole_sale_price": 11000,
    "retail_price": 12000,
    "options": [
      {
        "id": 235,
        "name": "Màu sắc",
        "position": 1
      },
      {
        "name": "Màu sắc sắc"
      }
    ]
  }
}
```
**Kết quả trả về**
```
{
    "product": {
        "id": 3939085,
        "tenant_id": 56322,
        "created_on": "2018-07-25T06:52:17Z",
        "modified_on": "2018-07-25T06:55:32Z",
        "status": "active",
        "brand_id": 130704,
        "brand": "Thám tử lừng danh Conan",
        "description": "Truyện trinh thám",
        "image_path": null,
        "image_name": null,
        "name": "Thám tử lừng danh Conan",
        "opt1": "Màu sắc",
        "opt2": "Màu sắc sắc",
        "opt3": null,
        "category": null,
        "category_code": null,
        "quantity": 3,
        "tags": "tags1",
        "available": null,
        "supplier_ids": [],
        "supplier": null,
        "supplier_id": 0,
        "variant_ids": [
            5702363,
            5702364,
            5702365
        ],
        "variants": [
            {
                "id": 5702363,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:55:32Z",
                "category_id": null,
                "brand_id": 130704,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "Thám tử lừng danh Conan",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP12",
                "barcode": "SP12",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "gói",
                "packsize": false,
                "packsize_quantity": null,
                "packsize_root_id": null,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702363,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 15,
                        "available": 15,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702364,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:55:32Z",
                "category_id": null,
                "brand_id": 130704,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "Thám tử lừng danh Conan",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP13",
                "barcode": "SP13",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng bé",
                "packsize": true,
                "packsize_quantity": 6,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702364,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 2.5,
                        "available": 2.5,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            },
            {
                "id": 5702365,
                "tenant_id": 56322,
                "location_id": 58369,
                "created_on": "2018-07-25T06:52:17Z",
                "modified_on": "2018-07-25T06:55:32Z",
                "category_id": null,
                "brand_id": 130704,
                "product_id": 3939085,
                "committed_stock": null,
                "incoming_stock": null,
                "composite": false,
                "description": null,
                "keep_selling": true,
                "last_cost_price": null,
                "retail_price": null,
                "init_price": 20000,
                "init_stock": 15,
                "max_online": null,
                "variant_retail_price": null,
                "variant_whole_price": null,
                "variant_import_price": null,
                "image_path": null,
                "image_name": null,
                "image_full_path": null,
                "image_id": null,
                "moving_average_cost": null,
                "name": "sp test unit 01",
                "online_ordering": true,
                "opt1": "M",
                "opt2": null,
                "opt3": null,
                "product_name": "Thám tử lừng danh Conan",
                "product_status": null,
                "status": "active",
                "sellable": true,
                "sku": "SP14",
                "barcode": "SP14",
                "stock_on_hand": null,
                "available": null,
                "supplier_code": null,
                "taxable": true,
                "weight_value": null,
                "weight_unit": null,
                "unit": "thùng to",
                "packsize": true,
                "packsize_quantity": 24,
                "packsize_root_id": 5702363,
                "image_ids": [],
                "variant_channels": null,
                "variant_prices": [],
                "inventories": [
                    {
                        "location_id": 58369,
                        "variant_id": 5702365,
                        "mac": 20000,
                        "amount": 0,
                        "on_hand": 0.625,
                        "available": 0.625,
                        "committed": 0,
                        "incoming": 0,
                        "onway": 0,
                        "reorder_point": 0,
                        "name": null,
                        "min_value": 0,
                        "max_value": 0,
                        "bin_location": null
                    }
                ],
                "images": [],
                "online": false
            }
        ],
        "options": [
            {
                "id": 4276732,
                "name": "Màu sắc",
                "position": 1
            },
            {
                "id": 4276748,
                "name": "Màu sắc sắc",
                "position": 2
            }
        ]
    }
}
```
<a name="delete-product_id"></a>
## 1.5 Xóa 1 sản phẩm (xóa cả variant và option)
**Request**
```
DELETE /admin/products/425 HTTP/1.1
Token: X-Sapo-Access-Token 28a48cee892343b2b29780a586c5ded2
Content-Type: application/json

```
**Kết quả trả về**
```
Status 200 OK
```
**Trường hợp có lỗi**
```
{
    "data_error": {
        "status": 422,
        "errors": {
            "product": "not exists Product: 393985"
        }
    }
}
```
