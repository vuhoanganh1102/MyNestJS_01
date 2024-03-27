﻿# Api TMDT

## Customers

- Đăng kí: <mark>Hanh<mark>

  POST api/customers/register

  req:

  ```bash
    {
          "user": "general",
          "password": "general",
          "address": "general",
          "phone": "general",
          "email": "general",
          "roleid":"general"
    }
  ```

  res:

  ```bash
    User đăng kí thành công.
    {
          "statuscode":201,
          "status": "Successfully inserted customer.",
          "tokens": "...."
    }
    Có username trong database
    {
            "statuscode":400,
            "status":"Username already exists."
    }
    Email đã tồn tại trong database
    {
            "statuscode":400,
            "status":"Email already exists."
    }
  ```

- Hiển thị tất cả các role cho khách hàng chọn: <mark> Vanh <mark>

  req:

  res:

  ```bash
  {
      "statuscode":200,
      "status":"Get Successfully.",
      "roleList":
      [
          "id":"general",
          "role":"general"
      ]
  }
  ```

- Khách hàng chọn role:<mark>Vanh<mark>

  GET customers/chooserole/{:id}

  req:

  ```bash
      {
          "id":"general"
      }
  ```

  res:

  ```bash
      {
          "statuscode":200,
          "status": "Successfully inserted role.",
      }
  ```

- Đăng nhập: <mark>Hanh<mark>

  POST /customers/login

  req:

  ```bash
    {
        "username":"",
        "password":""
    }
  ```

  res:

  ```bash
  Đúng mk user
  {
        "statuscode":200,
        "status":"Successfully logined.",
        "token":"..."
  }
  Sai mk
  {
        "statuscode":401,
        "status":"wrong password."
  }
  Không tồn tại user
  {
        "statuscode":401,
        "status":"unavailble user."
  }
  ```

* Xem lịch sử mua hàng:<mark>Vanh<mark>

  GET customers/getallorders/{:customerid}

  req:

  ```bash
  {
        "customerid":"general"
  }
  ```

  res:

  ```bash
  {
        "customerid":"general",
        "date":"general",
        "total":"general",
  }
  ```

* Xem chi tiết lịch sử mua hàng:

  GET customers/getorderdetail/{:orderid}

  req:

  ```bash
  {
        "orderid":"general"
  }
  ```

  res:

  ```bash
  {
        "date":"general",
        "total":"general",
        "orderDetailList":
        [
            "id":"..",
            "productId":"...",
            "quantity":"..",
            "name":"..",
            "price":"..",
            "discount":"..",
            "image":".."
        ]

  }
  ```

* Xem Cart:

  GET customers/getcart/{:cutomerid}

  ```bash
  {
        "customerid":"general"
  }
  ```

  res:

  ```bash
  {
        "customerid":"general",
        "date":"general",
        "total":"general",
        "orderDetailList":
        [
            "id":"..",
            "productId":"...",
            "quantity":"..",
            "name":"..",
            "price":"..",
            "discount":"..",
            "image":".."
        ]
  }

  ```

* Checkout:

  PATCH customers/checkout

  req:

  ```bash
  {
        "customerid":"general",
        "orderid":"...",
  }
  ```

  res:

  ```bash
  {
        "statuscode":200,
        "status":"Successfully checkout."
  }
  ```

## Product

- Lấy danh sách các category:

  GET products/categoryList

  req:

  ```bash
  {}
  ```

  res:

  ```bash
  {
        "id":",,,",
        "name":"..."
  }
  ```

- Thêm mới sản phẩm:

  POST products/addproduct

  req:

  ```bash
  {
        "des":"...",
        "quantity":"..",
        "name":"..",
        "price":"..",
        "discount":"..",
        "image":"..",
        "categoryid":".."
  }
  ```

  res:

  ```bash
  {
    "statuscode":201,
    "status":"Successfully created."
  }
  'Không tạo được do thiếu trường'
  {
    "statuscode":"401",
    "status":"miss attribute."
  }
  ```

- Xóa sản phẩm: PATCH products/deleteproduct/{:id}
- Sửa các thông tin sản phẩm: PATCH products/changeinforproduct/{:id}
- upload ảnh cho sản phẩm: POSt uploadfile/addfile
- Xem tất cả sản phẩm: GET products/getallproduct
- Tìm kiếm sản phẩm : GET products/getproducts/?category=&name=&price=
-
