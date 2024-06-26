# Api TMDT

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

- Hiển thị tất cả các role cho khách hàng chọn:

  GET customers/allroles

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

  GET api/orders/:customerid

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

  GET api/orderdetail/:orderid

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

  GET api/cart/:cutomerid

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

  PATCH api/checkout

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

  GET api/categorylist

  req:

  ```bash
  {}
  ```

  res:

  ```bash

  {
      [
        {
          "id":",,,",
          "name":"..."
        },....
      ]
  }
  ```

- Thêm mới sản phẩm:

  POST api/products

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

- Sửa các thông tin sản phẩm:

  PATCH api/products/:id

  req:

  ```bash
  {
      "id":"....",
      '/// có thể thay đổi các 1 hoặc tất cả các thuộc tính cuae products tru id'

  }
  ```

  res:

  ```bash
  {
      "statuscode":200,
      "status":"Successfully changed information."
  }
  ```

- upload ảnh cho sản phẩm:
  POSt api/mutipleimages

  req:

  ```bash
  {
      "Productid":"...",
      "local":"..."
  }
  ```

  res:

  ```bash
  {
      "statuscode":200,
      "status":"Successfully uploaded."
  }
  ```

- Xem tất cả sản phẩm:

  GET api/allproduct

  req:

  ```bash
  {}
  ```

  res:

  ```bash
  {
      "statuscode":200,
      "status":"Successfully.",
      "productlist":[
          {
            'các thuộc tính của product và categoryname'
          }
      ]
  }
  ```

- Tìm kiếm sản phẩm :

  GET api/products/?categoryid=&name=&price=

  req:

  ```bash
  {
      "category":"...",
      "name":"...",
      "price":"..."
  }
  ```

  res:

  ```bash
  {
      "statuscode":200,
      "status":"Successfully.",
      "product":{
          'các thuộc tính của product'
      }
  }
  ```

- Xem chi tiết sản phẩm:

  GET api/products/:id

  res:

  ```bash
  {
      'các thuôjc tính của sp'
  }
  ```
