# E-Commerce Server

Base url: <http://localhost:3000>

## **Register Admin**

Return json user object

-   **URL**

    /admin

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `first_name=[string]`\
      `username=[string]`\
      `password=[string]`\
      `email=[string]`

      **Optional:**

      `last_name=[string]`\
      `phone_number=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 272,
          "email": "hansin91@gmail.com",
          "username": "hansin1991",
          "message": "USER_CREATED"
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
            "First name is required",
            "Username is required"
          ]
        }
        ```

     -  **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "UNIQUE_VALIDATION",
          "errors": [
            "email must be unique"
          ]
        }
        ```

    -  **Code:** 400 BAD REQUEST <br />
      **Content:**
      ```json
      {
        "name": "BAD REQUEST",
        "message": "INPUT_ERROR",
        "errors": [
          "Username has minimal 6 characters",
          "Password has minimum 8 characters"
        ]
      }
      ```

## **Login Admin**

Returns json access token and message when admin login successfully

-   **URL**

    /admin/login

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `email=[string]`\
      `password=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MjcxLCJlbWFpbCI6ImhhbnNpbnN1c2F0eWFAZ21haWwuY29tIiwidXNlcm5hbWUiOiJoYW5zaW45MSIsInJvbGUiOnsiaWQiOjEsIm5hbWUiOiJBZG1pbiIsImNyZWF0ZWRBdCI6IjIwMjAtMDItMjJUMDg6NDQ6NTIuMjEwWiIsInVwZGF0ZWRBdCI6IjIwMjAtMDItMjJUMDg6NDQ6NTIuMjEwWiJ9LCJpYXQiOjE1ODI0NTUyNTl9.5q2rnJbwz6j7Cu82j7lDqLFRU1ndkrCTGcnr4nEx3GQ",
          "message": "LOGIN_SUCCESS"
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Email / password is incorrect"
        }
        ```

## **Get categories**

Returns json categories

-   **URL**

    /categories

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

    None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        [
          {
              "id": 223,
              "name": "Seal",
              "path": "seal"
          },
          {
              "id": 224,
              "name": "Bearing",
              "path": "bearing"
          }
        ]
        ```

-   **Error Response:**

    -   **Code:** 500 INTERNAL SERVER ERROR <br />
        **Content:**
        ```json
        {
          "message": "Internal Server Error"
        }
        ```

## **Get category**

Returns json category

-   **URL**

    /categories/:id

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

     **Required:**

    `id=[integer]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 223,
          "name": "Seal",
          "path": "seal"
        }
        ```

-   **Error Response:**

    -   **Code:** 500 INTERNAL SERVER ERROR <br />
        **Content:**
        ```json
        {
          "message": "Internal Server Error"
        }
        ```
    -   **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Category is not found with id 2"
        }
        ```

## **Create category**

  Returns json data when admin create category

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /categories

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `name=[string]`\
    `path=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "data": {
            "id": 226,
            "name": "Nozzle",
            "path": "nozzle",
            "updatedAt": "2020-02-23T11:10:13.960Z",
            "createdAt": "2020-02-23T11:10:13.960Z"
          },
          "message": "CATEGORY_CREATED"
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Name is required"
          ]
        }
        ```
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**

        ```json
        {
          "name": "BAD REQUEST",
          "message": "UNIQUE_VALIDATION",
          "errors": [
              "name must be unique"
          ]
        }
        ```

     -  **Code:** 401 UNAUTHORIZED <br />
        **Content:**

        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```


## **Update Category**

  Returns json data when admin update category by id

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /categories/:id

-   **Method:**

    `PUT`

-   **URL Params**

    **Required:**

    `id=[integer]`

-   **Data Params**

    `name=[string]`\
    `path=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "data": {
            "id": 226,
            "name": "Propeller",
            "path": "propeller",
            "createdAt": "2020-02-23T11:10:13.960Z",
            "updatedAt": "2020-02-23T11:18:55.722Z"
          },
          "message": "CATEGORY_UPDATED"
        }
        ```

-   **Error Response:**

     -  **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Name is required"
          ]
        }
        ```

    - **Code:** 400 BAD REQUEST <br />
      **Content:**
      ```json
      {
        "name": "BAD REQUEST",
        "message": "UNIQUE_VALIDATION",
        "errors": [
            "name must be unique"
        ]
      }
      ```

    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```

## **Delete Category**

  Returns json data when admin delete category by id

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /categories/:id

-   **Method:**

    `DELETE`

-   **URL Params**

    **Required:**

    `id=[integer]`

-   **Data Params**

    None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "message": "CATEGORY_DELETED"
        }
        ```

-   **Error Response:**

     -  **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Category with id 1 is not found"
        }
        ```
     -  **Code:** 400 INVALID TOKEN <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```

## **Get Products**

  Returns json products

-   **URL**

    /products

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

    None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "products": [
          {
            "id": 190,
            "name": "Ball Bearing Hitachi",
            "price": 250000,
            "stock": 50,
            "description": "Ball Bearing Hitachi adalah salah satu jenis bearing yang berfungsi untuk membatasi gerak relatif antara dua atau lebih komponen mesin agar selalu bergerak pada arah yang diinginkan.",
            "weight": "0.50",
            "SKU": "BBH-001",
            "category_id": 224,
            "createdAt": "2020-02-23T11:47:57.075Z",
            "updatedAt": "2020-02-23T11:47:57.075Z",
            "Category": {
                "id": 224,
                "name": "Bearing",
                "path": "bearing",
                "createdAt": "2020-02-23T10:08:22.384Z",
                "updatedAt": "2020-02-23T10:08:22.384Z"
            },
            "ProductImages": [
                {
                    "id": 91,
                    "url": "https://i.imgur.com/aNBfIwC.jpg",
                    "title": "190-71shWvsC0NL._AC_SY450_.jpg",
                    "product_id": 190,
                    "delete_hash": "vkiCqej0ZxhW9Qv",
                    "createdAt": "2020-02-23T11:47:59.587Z",
                    "updatedAt": "2020-02-23T11:47:59.587Z"
                }
            ]
        },
        {
            "id": 189,
            "name": "Mesin Kapal - Marine Gearbox Rhino-06",
            "price": 4500000,
            "stock": 10,
            "description": "Marine Gearbox Rhino-06 merupakan salah satu mesin kapal atau marine gearbox yang mampu menghasilkan tenaga maksimal 12.5 HP dengan kecepatan perputaran mesin 2100 rpm. Mesin marine gearbox Rhino-06 ini memiliki berat mesin sebesar 69 kg dan center distance 124 mm. Mesin ini memiliki rated propeller thrust hingga 1.8 KN. Mesin marine gearbox Rhino-06 ini cocok digunakan untuk perlengkapan berlayar Anda.",
            "weight": "20.00",
            "SKU": "MGR-006",
            "category_id": 228,
            "createdAt": "2020-02-23T11:44:16.102Z",
            "updatedAt": "2020-02-23T11:44:47.782Z",
            "Category": {
                "id": 228,
                "name": "Gearbox",
                "path": "gearbox",
                "createdAt": "2020-02-23T11:44:39.642Z",
                "updatedAt": "2020-02-23T11:44:39.642Z"
            },
            "ProductImages": [
                {
                    "id": 90,
                    "url": "https://i.imgur.com/QbO90Jf.jpg",
                    "title": "189-s-l800.jpg",
                    "product_id": 189,
                    "delete_hash": "odAp3d4pJEtVcPF",
                    "createdAt": "2020-02-23T11:44:20.561Z",
                    "updatedAt": "2020-02-23T11:44:20.561Z"
                }
              ]
            }
          ]
        }
        ```

-   **Error Response:**

    -   **Code:** 500 INTERNAL SERVER ERROR <br />
        **Content:**
         ```json
        {
          "message": "Internal Server Error"
        }
        ```

## **Get Product**

  Returns json product

-   **URL**

    /products/:id

-   **Method:**

    `GET`

-   **URL Params**

    **Required:**

    `id=[integer]`

-   **Data Params**

     None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
        "product": {
            "id": 189,
            "name": "Mesin Kapal - Marine Gearbox Rhino-06",
            "price": 4500000,
            "stock": 10,
            "description": "Marine Gearbox Rhino-06 merupakan salah satu mesin kapal atau marine gearbox yang mampu menghasilkan tenaga maksimal 12.5 HP dengan kecepatan perputaran mesin 2100 rpm. Mesin marine gearbox Rhino-06 ini memiliki berat mesin sebesar 69 kg dan center distance 124 mm. Mesin ini memiliki rated propeller thrust hingga 1.8 KN. Mesin marine gearbox Rhino-06 ini cocok digunakan untuk perlengkapan berlayar Anda.",
            "weight": "20.00",
            "SKU": "MGR-006",
            "category_id": 228,
            "createdAt": "2020-02-23T11:44:16.102Z",
            "updatedAt": "2020-02-23T11:44:47.782Z",
            "Category": {
                "id": 228,
                "name": "Gearbox",
                "path": "gearbox",
                "createdAt": "2020-02-23T11:44:39.642Z",
                "updatedAt": "2020-02-23T11:44:39.642Z"
            },
            "ProductImages": [
              {
                "id": 90,
                "url": "https://i.imgur.com/QbO90Jf.jpg",
                "title": "189-s-l800.jpg",
                "product_id": 189,
                "delete_hash": "odAp3d4pJEtVcPF",
                "createdAt": "2020-02-23T11:44:20.561Z",
                "updatedAt": "2020-02-23T11:44:20.561Z"
              }
            ]
          }
        }
        ```

-   **Error Response:**

    -   **Code:** 500 INTERNAL SERVER ERROR <br />
        **Content:**
        ```json
        {
          "message": "Internal Server Error"
        }
        ```

    -   **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Product with id 1 not found"
        }
        ```

## **Create Product**

  Returns json new product

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /products

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `name=[string]`\
      `price=[integer]`\
      `stock=[integer]`\
      `category_id=[integer]`\
      `SKU=[string]`\
      `description=[string]`\
      `weight=[decimal]`

      **Optional**

      `productImages=[file]`

      ## Must use form data

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
        "product": {
            "id": 193,
            "name": "Filter Nozzel Lateral",
            "price": 350000,
            "stock": 5,
            "category_id": 229,
            "SKU": "FN-001",
            "description": "Nozzle Top dan Bottom K1 sebagai equipment pendukung dalam fabrikasi pressure vessel filter. Tersedia berbagai ukuran dan jenis sesuai dengan permintaan dan design kapasitas flow air. Strainer yang dipergunakan untuk design softener, demin dan mixed bed mempunyai slot yang lebih kecil yakni 0,2 mm, hal ini diperlukan untuk menjaga agar resin tidak lolos saat dilakukan backwash",
            "weight": "0.20",
            "updatedAt": "2020-02-23T12:15:06.697Z",
            "createdAt": "2020-02-23T12:15:06.697Z"
          }
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "UNIQUE_VALIDATION",
          "errors": [
              "name must be unique"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Stock minimal zero"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Name is required"
          ]
        }
        ```
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
    -   **Code:** 400 INVALID TOKEN <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

## **Update Product**

  Returns json updated product

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /products/:id

-   **Method:**

    `PUT`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `id=[integer]`\
      `name=[string]`\
      `price=[integer]`\
      `stock=[integer]`\
      `category_id=[integer]`\
      `SKU=[string]`\
      `description=[string]`\
      `weight=[decimal]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "product": {
            "id": 198,
            "name": "Saklar Clipsal",
            "price": 65000,
            "stock": 30,
            "category_id": 230,
            "createdAt": "2020-02-23T12:38:49.245Z",
            "updatedAt": "2020-02-23T12:46:04.443Z",
            "description": "Saklar merk Clipsal berkualitas tinggi dan awet sampai 3 tahun",
            "SKU": "CP-001",
            "weight": "0.10"
          }
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Price has to be greater than zero",
              "Price only contains number",
              "Stock only contains number"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "UNIQUE_VALIDATION",
          "errors": [
              "name must be unique"
          ]
        }
        ```
    -   **Code:** 400 LOGIN FAILED <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
    -   **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Product with id 11 is not found"
        }
        ```

## **Delete Product**

  Returns json message deleted product

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /products/:id

-   **Method:**

    `DELETE`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `id=[integer]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "message": "Delete product with id 199 successfully"
        }
        ```

-   **Error Response:**

    -   **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Product with id 199 is not found"
        }
        ```
    -   **Code:** 400 INVALID TOKEN <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```

## **Register User**

Return json user object

-   **URL**

    /users

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `first_name=[string]`\
      `username=[string]`\
      `password=[string]`\
      `email=[string]`

      **Optional:**

      `last_name=[string]`\
      `phone_number=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 272,
          "email": "hansin91@gmail.com",
          "username": "hansin1991",
          "message": "USER_CREATED"
        }
        ```

-   **Error Response:**

    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
            "First name is required",
            "Username is required"
          ]
        }
        ```

     -  **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "UNIQUE_VALIDATION",
          "errors": [
            "email must be unique"
          ]
        }
        ```

    -  **Code:** 400 BAD REQUEST <br />
      **Content:**
      ```json
      {
        "name": "BAD REQUEST",
        "message": "INPUT_ERROR",
        "errors": [
          "Username has minimal 6 characters",
          "Password has minimum 8 characters"
        ]
      }
      ```

## **Login User**

Returns json access token and message

-   **URL**

    /users/login

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

      **Required:**

      `email=[string]`\
      `password=[string]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MjcxLCJlbWFpbCI6ImhhbnNpbnN1c2F0eWFAZ21haWwuY29tIiwidXNlcm5hbWUiOiJoYW5zaW45MSIsInJvbGUiOnsiaWQiOjEsIm5hbWUiOiJBZG1pbiIsImNyZWF0ZWRBdCI6IjIwMjAtMDItMjJUMDg6NDQ6NTIuMjEwWiIsInVwZGF0ZWRBdCI6IjIwMjAtMDItMjJUMDg6NDQ6NTIuMjEwWiJ9LCJpYXQiOjE1ODI0NTUyNTl9.5q2rnJbwz6j7Cu82j7lDqLFRU1ndkrCTGcnr4nEx3GQ",
          "message": "LOGIN_SUCCESS"
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Email / password is incorrect"
        }
        ```

## **Find User**

Returns json user

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /users

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

     None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "first_name": "Handy",
          "last_name": "Handy",
          "username": "handy1990",
          "email": "handy@gmail.com",
          "cart": [],
          "phone_number": null
        }
        ```
        OR
        ```json
        {
          "first_name": "Handy",
          "last_name": "Handy",
          "username": "handy1990",
          "email": "handy@gmail.com",
          "cart": [
              {
                  "id": 23,
                  "user_id": 547,
                  "status": false,
                  "createdAt": "2020-02-27T11:15:01.668Z",
                  "updatedAt": "2020-02-27T11:15:01.668Z"
              }
          ],
          "phone_number": null
        }
      ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```

## **Get Cart**

Returns json cart includes cart details

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts/:id

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

    **Required**

    `id=[integer]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 28,
          "user_id": 547,
          "status": false,
          "createdAt": "2020-02-27T15:22:10.472Z",
          "updatedAt": "2020-02-27T15:22:10.472Z",
          "CartDetails": [
            {
              "id": 75,
              "cart_id": 28,
              "product_id": 340,
              "quantity": 1,
              "price": 95600,
              "total": 95600,
              "createdAt": "2020-02-27T15:22:10.479Z",
              "updatedAt": "2020-02-27T15:22:10.479Z",
              "Product": {
                "id": 340,
                "name": "NOK Standard Oil Seal TC Type",
                "price": 95600,
                "stock": 30,
                "description": "A rubber rotation seal (around the boundary) with a dust lip.",
                "weight": "0.50",
                "SKU": "NOK-TC-001",
                "category_id": 347,
                "createdAt": "2020-02-25T13:08:23.643Z",
                "updatedAt": "2020-02-27T08:25:49.582Z",
                "ProductImages": [
                    {
                        "id": 133,
                        "url": "https://i.imgur.com/MdLfUPk.jpg",
                        "title": "340-NOK1_221005008851.jpg",
                        "product_id": 340,
                        "delete_hash": "p7r0F6rVVoNh5iP",
                        "createdAt": "2020-02-25T13:08:25.518Z",
                        "updatedAt": "2020-02-25T13:08:25.518Z"
                    }
                  ]
                }
              }
            ]
          }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```

## **Create Cart**

Returns json new product added to cart

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `product_id=[integer]`\
    `quantity=[integer]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 73,
          "cart_id": 24,
          "product_id": 338,
          "quantity": 10,
          "price": 125000,
          "updatedAt": "2020-02-27T12:03:55.739Z",
          "createdAt": "2020-02-27T12:03:55.739Z",
          "total": 1250000
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "INPUT_ERROR",
          "errors": [
              "Quantity must be greather than zero"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```

## **Update Single Product In Cart**

Returns json product added to cart

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts/:id

-   **Method:**

    `PUT`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `id=[integer]`\
    `product_id=[integer]`\
    `quantity=[integer]`

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "id": 73,
          "cart_id": 24,
          "product_id": 338,
          "quantity": 14,
          "price": 125000,
          "total": 1750000,
          "createdAt": "2020-02-27T12:03:55.739Z",
          "updatedAt": "2020-02-27T14:35:51.966Z"
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD_REQUEST",
          "message": "INPUT_ERROR",
          "error": "Quantity must be greather than zero"
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```


-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```

## **Get History Transactions**

Returns json history carts include cart details

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts

-   **Method:**

    `GET`

-   **URL Params**

    None

-   **Data Params**

    None

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        [
          {
            "id": 30,
            "user_id": 547,
            "status": true,
            "createdAt": "2020-02-27T16:17:14.987Z",
            "updatedAt": "2020-02-27T16:17:21.117Z",
            "CartDetails": [
              {
                "id": 80,
                "cart_id": 30,
                "product_id": 340,
                "quantity": 1,
                "price": 95600,
                "total": 95600,
                "createdAt": "2020-02-27T16:17:14.995Z",
                "updatedAt": "2020-02-27T16:17:14.995Z",
                "Product": {
                    "id": 340,
                    "name": "NOK Standard Oil Seal TC Type",
                    "price": 95600,
                    "stock": 28,
                    "description": "A rubber rotation seal (around the boundary) with a dust lip.",
                    "weight": "0.50",
                    "SKU": "NOK-TC-001",
                    "category_id": 347,
                    "createdAt": "2020-02-25T13:08:23.643Z",
                    "updatedAt": "2020-02-27T16:17:21.131Z"
                }
            },
            {
                "id": 81,
                "cart_id": 30,
                "product_id": 341,
                "quantity": 1,
                "price": 250000,
                "total": 250000,
                "createdAt": "2020-02-27T16:17:15.809Z",
                "updatedAt": "2020-02-27T16:17:15.809Z",
                "Product": {
                    "id": 341,
                    "name": "NOK Standard Oil Seal SC Type",
                    "price": 250000,
                    "stock": 7,
                    "description": "Seal, Single Lip, Outer Periphery Rubber for Rotation.",
                    "weight": "1.50",
                    "SKU": "NOK-SC-001",
                    "category_id": 347,
                    "createdAt": "2020-02-25T13:13:00.436Z",
                    "updatedAt": "2020-02-27T16:17:21.137Z"
                }
            }
          ]
        },
        {
          "id": 28,
          "user_id": 547,
          "status": true,
          "createdAt": "2020-02-27T15:22:10.472Z",
          "updatedAt": "2020-02-27T16:16:53.886Z",
          "CartDetails": [
            {
                "id": 75,
                "cart_id": 28,
                "product_id": 340,
                "quantity": 1,
                "price": 95600,
                "total": 95600,
                "createdAt": "2020-02-27T15:22:10.479Z",
                "updatedAt": "2020-02-27T15:22:10.479Z",
                "Product": {
                    "id": 340,
                    "name": "NOK Standard Oil Seal TC Type",
                    "price": 95600,
                    "stock": 28,
                    "description": "A rubber rotation seal (around the boundary) with a dust lip.",
                    "weight": "0.50",
                    "SKU": "NOK-TC-001",
                    "category_id": 347,
                    "createdAt": "2020-02-25T13:08:23.643Z",
                    "updatedAt": "2020-02-27T16:17:21.131Z"
                }
            },
            {
                "id": 78,
                "cart_id": 28,
                "product_id": 338,
                "quantity": 1,
                "price": 125000,
                "total": 125000,
                "createdAt": "2020-02-27T16:04:58.541Z",
                "updatedAt": "2020-02-27T16:04:58.541Z",
                "Product": {
                    "id": 338,
                    "name": "Deep Groove Ball Bearings",
                    "price": 125000,
                    "stock": 8,
                    "description": "The raceway of the deep groove ball bearing includes arc-shaped deep grooves for both the inner and outer rings and can support radial loads, axial loads in both directions, and synthetic loads, and are also ideal for high-speed rotation applications.",
                    "weight": "2.00",
                    "SKU": "DGB-001",
                    "category_id": 345,
                    "createdAt": "2020-02-25T13:02:41.000Z",
                    "updatedAt": "2020-02-27T16:16:53.936Z"
                }
            },
            {
                "id": 79,
                "cart_id": 28,
                "product_id": 338,
                "quantity": 1,
                "price": 125000,
                "total": 125000,
                "createdAt": "2020-02-27T16:05:57.960Z",
                "updatedAt": "2020-02-27T16:05:57.960Z",
                "Product": {
                    "id": 338,
                    "name": "Deep Groove Ball Bearings",
                    "price": 125000,
                    "stock": 8,
                    "description": "The raceway of the deep groove ball bearing includes arc-shaped deep grooves for both the inner and outer rings and can support radial loads, axial loads in both directions, and synthetic loads, and are also ideal for high-speed rotation applications.",
                    "weight": "2.00",
                    "SKU": "DGB-001",
                    "category_id": 345,
                    "createdAt": "2020-02-25T13:02:41.000Z",
                    "updatedAt": "2020-02-27T16:16:53.936Z"
                }
            },
            {
                "id": 77,
                "cart_id": 28,
                "product_id": 338,
                "quantity": 2,
                "price": 125000,
                "total": 250000,
                "createdAt": "2020-02-27T16:04:23.745Z",
                "updatedAt": "2020-02-27T16:09:04.522Z",
                "Product": {
                    "id": 338,
                    "name": "Deep Groove Ball Bearings",
                    "price": 125000,
                    "stock": 8,
                    "description": "The raceway of the deep groove ball bearing includes arc-shaped deep grooves for both the inner and outer rings and can support radial loads, axial loads in both directions, and synthetic loads, and are also ideal for high-speed rotation applications.",
                    "weight": "2.00",
                    "SKU": "DGB-001",
                    "category_id": 345,
                    "createdAt": "2020-02-25T13:02:41.000Z",
                    "updatedAt": "2020-02-27T16:16:53.936Z"
                  }
                }
              ]
            }
          ]
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```

## **Update All Product In Cart**

Returns json all updated product

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts/:id/all

-   **Method:**

    `PUT`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `id=[integer]`\
    `cart_details=[array]`\

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        [
          {
              "id":85,
              "cart_id":31,
              "product_id":339,
              "quantity":1,
              "price":150000,
              "total":150000,
              "createdAt":"2020-02-27T21:16:54.272Z",
              "updatedAt":"2020-02-27T21:28:24.810Z"
          },
          {
              "id":82,
              "cart_id":31,
              "product_id":340,
              "quantity":2,
              "price":95600,
              "total":191200,
              "createdAt":"2020-02-27T20:29:25.721Z",
              "updatedAt":"2020-02-27T21:28:24.811Z"
          }
        ]
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name":"BAD REQUEST",
          "message":"INPUT_ERROR",
          "errors":[
              "Quantity must be greather than zero"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```

## **Delete Product In Cart**

Returns json message

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts/:id/:detail_id

-   **Method:**

    `DELETE`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `id=[integer]`\
    `detail_id=[integer]`\

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "message": "Delete successfully"
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```
-   **Error Response:**
    -   **Code:** 404 NOT FOUND <br />
        **Content:**
        ```json
        {
          "name": "NOT_FOUND",
          "error": "Car detail with id 84 is not found"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```

## **Checkout Cart**

Returns json message

- **Headers**

    Authorization: Bearer `<token>`

-   **URL**

    /carts/:id

-   **Method:**

    `POST`

-   **URL Params**

    None

-   **Data Params**

    **Required:**

    `id=[integer]`\
    `cart_details=[array]`\

-   **Success Response:**

    -   **Code:** 200 <br />
        **Content:**
        ```json
        {
          "message": "Your order has been successfully placed"
        }
        ```

-   **Error Response:**
    -   **Code:** 400 BAD REQUEST <br />
        **Content:**
        ```json
        {
          "name":"NOT_ENOUGH_STOCK",
          "message":"Not enough stock",
          "errors":[
              "not enough stock NOK Standard Oil Seal SC Type",
              "not enough stock Deep Groove Ball Bearings"
          ]
        }
        ```
        OR
        ```json
        {
          "name": "BAD REQUEST",
          "message": "LOGIN_FAILED",
          "error": "Please login first"
        }
        ```

-   **Error Response:**
    -   **Code:** 401 UNAUTHORIZED <br />
        **Content:**
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "Please login first"
        }
        ```
        OR
        ```json
        {
          "name": "UNAUTHORIZED",
          "message": "You are not authorized to access this cart",
          "error": "You are not authorized to access this cart"
        }
        ```