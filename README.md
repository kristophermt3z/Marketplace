# Marketplace Application - Functional Documentation

## Technical documentation
- Is located inside the Frontend and Backend repos; each one has its own documentation.

## Links

- **Production Link**: [Marketplace Production](https://marketplace-salvadormartinez.netlify.app/)
- **Frontend Repository  (technical documentation is inside)**: [Marketplace Frontend](https://github.com/salvadormartin3z/Marketplace-Frontend)
- **Backend Repository  (technical documentation is inside)**: [Marketplace Backend](https://github.com/salvadormartin3z/Marketplace-Backend)


## Admin Account
- Email: admin@admin.com
- Password: 123admin

## Description

The Marketplace Application is designed to connect sellers with potential buyers. It offers functionalities for sellers to register, list products, while buyers can browse and filter through available products. Additionally, administrators can oversee the marketplace and filter through sellers.
![image](https://github.com/user-attachments/assets/f065e646-851a-4475-a9b7-9e6c38a67076)
![image](https://github.com/user-attachments/assets/e91147be-9ae4-415d-95aa-0be02d78d835)


### Seller

- **Account Creation**: Sellers can create an account using their email to access the Marketplace.
  - A modal allows sellers to input their email, password, and password confirmation.
  - If the password and confirmation do not match, an error message is displayed.
  - If the user already exists, an alert displays the error.
  - Successful account creation closes the modal.

- **Product Registration**: Sellers can register products and assign prices for customers to view.
  - Products can be created with a name, SKU, quantity, and price. An error indicates any missing attributes.
  - Only authenticated users can upload products.

- **Product Management**: Sellers can view and manage all the products they have registered.
  - Each seller can only view products they have listed.
  - Access to this screen requires user authentication.
 
-![image](https://github.com/user-attachments/assets/8c5111bd-d1fb-4bb1-ad84-5a0194eac3c2)
![image](https://github.com/user-attachments/assets/ea9a1fe2-7e03-4958-b855-ae358f15a874)
![image](https://github.com/user-attachments/assets/26c5e76d-7fc7-443c-a802-3d62ed2b0797)



### Buyer

- **Product Search**: Buyers can search for products to add to their shopping cart.
  - Products can be filtered by name, SKU, and/or price range.
  - ![image](https://github.com/user-attachments/assets/977e3656-ea41-4670-ab7e-74ed1e681e64)


### Administrator

- **Product Oversight**: Administrators can view all products registered on the marketplace.
  - Products can be filtered by the seller.
  - Access to this screen requires user authentication.
 
![image](https://github.com/user-attachments/assets/7f456bfd-faed-453d-b3a0-f70c212d8318)


## Route Protection

The application ensures route protection through authentication. Only authenticated users can access certain features:

- **Sellers** can register and manage products only when logged in.
- **Administrators** can view and filter all products on the platform when logged in.

Route protection is implemented using middleware that verifies user tokens and checks user roles to determine access levels.

## Database Structure

The database consists of two main tables: `vendedores` and `products`.

### vendedores

| Column    | Type     | Description                                  |
|-----------|----------|----------------------------------------------|
| id        | SERIAL   | Primary key                                  |
| email     | VARCHAR  | Unique email address                         |
| password  | VARCHAR  | Hashed password for authentication           |
| role      | VARCHAR  | User role (e.g., 'vendedor', 'admin')        |

### products

| Column    | Type     | Description                                  |
|-----------|----------|----------------------------------------------|
| id        | SERIAL   | Primary key                                  |
| name      | VARCHAR  | Name of the product                          |
| sku       | VARCHAR  | Unique SKU identifier                        |
| quantity  | INT      | Quantity available                           |
| price     | DECIMAL  | Price of the product                         |
| seller_id | INT      | Foreign key referencing `vendedores(id)`     |

The `vendedores` table stores user information, while the `products` table stores product details associated with a seller.


