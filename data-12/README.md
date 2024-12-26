# Database Access

This project accessing a relational database. The purpose of this project is to demonstrate how to work with a MySQL database using Go, including performing CRUD (Create, Read, Update, Delete) operations effectively.

## Getting Started

1. **Install [Go](https://go.dev/dl/) and [MySQL](https://dev.mysql.com/downloads/) or [Dependencies](github.com/go-sql-driver/mysql)**

2. **Clone this repository**

   ```
   git clone https://github.com/ranabel/Web-Application-Go/data-12.git
   ```

3. **Setup Database**

   Setup database using MySQL and run this script, before it, login to MySQL with `mysql -u root -p` :

    ```
    CREATE DATABASE albumdb;
    USE albumdb;
    ```

   and on `data.sql` execute the sql file with command source

    ```
    DROP TABLE IF EXISTS album;
    CREATE TABLE album (
      id         INT AUTO_INCREMENT NOT NULL,
      title      VARCHAR(128) NOT NULL,
      artist     VARCHAR(255) NOT NULL,
      price      DECIMAL(5,2) NOT NULL,
      PRIMARY KEY (`id`)
    );

    INSERT INTO album
      (title, artist, price)
    VALUES
      ('Blue Train', 'John Coltrane', 56.99),
      ('Giant Steps', 'John Coltrane', 63.99),
      ('Jeru', 'Gerry Mulligan', 17.99),
      ('Sarah Vaughan', 'Sarah Vaughan', 34.98);
    ```
  
    set environment variables with DBUSER and DBPASS, generally using user root and pwd enter just blank.

4. **Run this Application**

    ```
    go run main.go
    ```

## CRUD
- **Create**: Add a new album to the database.  
- **Read**:  
  - Display all albums.  
  - Show album details based on the ID.  
- **Update**: Update album information based on the ID.  
- **Delete**: Delete an album based on the ID.  


## Album Management API Documentation

### **1. Display All Albums**
- **URL**: `/albums`
- **Method**: `GET`
- **Response**:
  ```json
  [
    {
      "id": 1,
      "title": "info album",
      "artist": "info artise",
      "price": 53.35
    }
  ]
  ```

### **2. Display Album by ID**
- **URL**: `/album?id={id}`
- **Method**: `GET`
- **Response**:
  ```json
  {
    "id": 1,
    "title": "info album",
    "artist": "info artise",
    "price": 53.35
  }
  ```

### **3. Add a New Album**
- **URL**: `/albums`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "title": "detected",
    "artist": "nuel",
    "price": 11.26
  }
  ```
- **Response**:
  ```json
  {
    "id": 2,
    "title": "detected",
    "artist": "nuel",
    "price": 11.26
  }
  ```

### **4. Update an Album**
- **URL**: `/album?id={id}` example 4
- **Method**: `PUT`
- **Request Body**:
  ```json
  {
    "title": "apa",
    "artist": "siapa",
    "price": 44.44
  }
  ```
- **Response**:
  ```
  Album with ID 4 updated successfully
  ```

### **5. Delete an Album**
- **URL**: `/album?id={id}` example 7
- **Method**: `DELETE`
- **Response**:
  ```
  Album with ID 7 deleted successfully
  ```