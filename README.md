# Api TMDT

## Customers

- Đăng kí: POST /customers/register

  req:

  ```bash
      {
          "user": "general",
          "password": "general",
          "address": "general",
          "phone": "general",
          "email": "general",
      }
  ```

  res:

  ```bash
      {
          "statuscode":200,
          "status": "Successfully inserted customer.",
      }
  ```

- Khách hàng chọn role: POST customers/chooserole
  req:
  ```bash
      {
          "uuid": "general",
          "roleid": "general"
      }
  ```
  res:
  ```bash
      {
          "statuscode":200,
          "status": "Successfully inserted role.",
          "tokens": "...."
      }
  ```
- Kiểm tra xem đã tồn tại email trong db chưa: GET /customer/checkemail
  req:
  ```bash
      {
          "uuid" : "general",
          "email": "general"
      }
  ```
  res:
  ```bash
      {
          "statuscode":boolean,
          "status": "general",
      }
  ```
- Kiểm tra xem đã tồn tại username trong db chưa: GET /customer/checkusername
  req:
  ```bash
      {
          "uuid" : "general",
          "email": "general"
      }
  ```
  res:
  ```bash
      {
          "statuscode":boolean,
          "status": "general",
      }
  ```
- Đăng nhập: POST /customers/login

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
* Xem lịch sử mua hàng: GET customers/getallorders
* Xem Cart: GET customers/getcart
* Checkout: PATCH customers/checkout
## Product

- Thêm mới sản phẩm: POST products/addproduct
- Xóa sản phẩm: PATCH products/deleteproduct/{:id}
- Sửa các thông tin sản phẩm: PATCH products/changeinforproduct/{:id}
- upload ảnh cho sản phẩm: POSt uploadfile/addfile
- Xem tất cả sản phẩm: GET products/getallproduct
- Tìm kiếm sản phẩm : GET products/getproducts/?category=&name=&price=
- 
