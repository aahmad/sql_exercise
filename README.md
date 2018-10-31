# SQL Exercises

The purpose of this repo is to demonstrate some basic to intermediate SQL examples. 

## Schema 
The schema is as follows:


```

--------------------               ------------------           ------------------
|                  |               |                |           |                |
|       users      |-------------->|    orders      |           |    products    |
|                  |               |                |           |                |
--------------------               ------------------           ------------------
                                          |                             |
                                          |                             |
                                          |                             |
                                          V                             |
                                   ---------------------                |
                                   |                   | <--------------|             
                                   |  orders_products  |               
                                   |                   |               
                                   ---------------------             
                                   
```

The SQL is as follows:

```
CREATE TABLE users (
    user_id     SERIAL    PRIMARY KEY
  , first_name  TEXT
  , last_name   TEXT
);

CREATE TABLE orders (
     order_id   SERIAL       PRIMARY KEY
   , user_id    INTEGER      REFERENCES users
   , amount     NUMERIC(9,2)
);

CREATE TABLE products (
    product_id  SERIAL       PRIMARY KEY
  , name        TEXT
  , unit_price  NUMERIC(9,2)
);

CREATE TABLE orders_products (
    orders_product_id  SERIAL       PRIMARY KEY
  , order_id           INTEGER      REFERENCES orders
  , product_id         INTEGER      REFERENCES products
  , quantity           INTEGER
  , cost               NUMERIC(9,2)
);

```

## Setup

```
$ createdb sql_exercise
$ psql sql_exercise < schema/sql_exercise.sql
```
