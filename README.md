# DatabaseTesting_Group3Midterm
# Online Book Store
###### The following project will consist of the design aspects of an Online Booke Store, that will be equipped with audio books, electronic books as well as physical books. The system will include Authors, publishers and customers, the customers will be able to browse through the catalog of the online book store, they will be able to purchase these books and leave reviews based on their purchases. 

## Responsibilities

* Akash Balan: Creating the database, DDL/DML
* Saju: Book Store Requirements
* Ruwini: Typescript

## Database Schema
###### The Database Schema will consist of the table information such as table names, fields, datatypes and the relationship between these entities, it will ask given an idea about the primary keys and foreign keys utilized in the system. The tables below will indicate name of the colmuns, The datatypes and if the corresponding attribute is a primary key or a foreign key.

### Authors

| Name              | Data type | PK/FK |
| -------------     |:----------|:-----:|
| author_id         | INT       | PK    |
| author_name       | VARCHAR   |       |
| author_biogragphy | TEXT      |       |
| author_DOB        | DATE      |       |

### Publishers

| Name              | Data type | PK/FK |
| -------------     |:----------|:-----:|
| publisher_id      | INT       | PK    |
| publisher_name    | VARCHAR   |       |
| publisher_address | VARCHAR   |       |
| publisher_website | VARCHAR   |       |

### Books

| Name              | Data type | PK/FK |
| ------------------|:----------|:-----:|
| book_id           | INT       | PK    |
| book_title        | VARCHAR   |       |
| book_genre        | VARCHAR   |       |
| book_publish_date | DATE      |       |
| author_id         | INT       | FK    |
| publisher_id      | INT       | FK    |
| book_format       | VARCHAR   |       |

### Customers

| Name                       | Data type | PK/FK |
| ---------------------------|:----------|:-----:|
| customer_id                | INT       | PK    |
| customer_name              | VARCHAR   |       |
| customer_email             | VARCHAR   |       |
| customer_registration_date | DATE      |       |

### Orders

| Name               | Data type | PK/FK |
| ------------------ |:----------|:-----:|
| order_id           | INT       | PK    |
| customer_id        | INT       | FK    |
| order_date         | DATE      |       |
| order_total_amount | DECIMAL   |       |

### OrderItems

| Name               | Data type | PK/FK |
| ------------------ |:----------|:-----:|
| order_item_id      | INT       | PK    |
| order_id           | INT       | FK    |
| book_id            | INT       | FK    |
| order_item_quantity| INT       |       |
| order_item_price   | DECIMAL   |       |

### Reviews

| Name               | Data type | PK/FK |
| ------------------ |:----------|:-----:|
| review_id          | INT       | PK    |
| book_id            | INT       | FK    |
| customer_id        | INT       | FK    |
| review_rating      | INT       |       |
| review_comment     | TEXT      |       |
| review_date        | DATE      |       |

## SQL Queries
###### Authors
```
CREATE TABLE Authors (
    author_id INT PRIMARY KEY,
    author_name VARCHAR(100),
    author_biography TEXT,
    author_DOB DATE
);

```
###### Publishers
```
CREATE TABLE Publishers (
    publisher_id INT PRIMARY KEY,
    publisher_name VARCHAR(100),
    publisher_address VARCHAR(255),
    publisher_website VARCHAR(100)
);

```
###### Books
```
CREATE TABLE Books (
    book_id INT PRIMARY KEY,
    book_title VARCHAR(100),
    book_genre VARCHAR(50),
    book_publish_date DATE,
    author_id INT,
    publisher_id INT,
    book_format VARCHAR(10) CHECK (book_format IN ('Physical', 'E-Book', 'Audiobook')),
    FOREIGN KEY (author_id) REFERENCES Authors(author_id),
    FOREIGN KEY (publisher_id) REFERENCES Publishers(publisher_id)
);

```
###### Customers
```
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100),
    customer_email VARCHAR(100),
    customer_registration_date DATE
);

```
###### Orders
```
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    order_total_amount DECIMAL(10, 2),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

```
###### OrderItems 
```
CREATE TABLE OrderItems (
    order_item_id INT PRIMARY KEY,
    order_id INT,
    book_id INT,
    order_item_quantity INT,
    order_item_price DECIMAL(10, 2),
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (book_id) REFERENCES Books(book_id)
);

```
###### Reviews 
```
CREATE TABLE Reviews (
    review_id INT PRIMARY KEY,
    book_id INT,
    customer_id INT,
    review_rating INT,
    review_comment TEXT,
    review_date DATE,
    FOREIGN KEY (book_id) REFERENCES Books(book_id),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

```
## DDL/DML for Customers table
###### DDL
```
CREATE TABLE Customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100),
    customer_email VARCHAR(100),
    customer_registration_date DATE
);

```
###### DML
```
INSERT INTO Customers (customer_id, customer_name, customer_email, customer_registration_date)
VALUES 
(1, 'Akash Balan', 'akashbalan@example.com', '2024-06-26'),
(2, 'Saju', 'saju@example.com', '2024-06-25'),
(3, 'Ruwini', 'ruwini@example.com', '2024-06-24'),
(4, 'Wang', 'wang@example.com', '2024-06-23');

```
## Additional BookStore Requirements

