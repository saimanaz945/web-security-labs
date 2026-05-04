
# Tautology-Based SQL Injection (Data Disclosure)

This repository demonstrates how a simple SQL injection payload can be used to bypass application logic—specifically a "hidden" status on products—to reveal all items in a database regardless of their intended visibility.

## The Vulnerability
The application uses a `category` filter in the URL to display specific products. The back-end query likely looks like this:

```sql
SELECT * FROM products WHERE category = 'Gifts' AND released = 1
```

By injecting a tautology (`OR 1=1`), we force the `WHERE` clause to always evaluate as **True**, effectively ignoring the `released = 1` requirement.

## Payloads
| Payload | Targeted Database |
| :--- | :--- |
| `filter?category=Gifts' OR 1=1--` | MySQL / PostgreSQL |
| `filter?category=Gifts' OR 1=1--+` | URL-encoded MySQL (The `+` acts as a space) |
| `filter?category=Gifts' OR 1=1--` | MS SQL Server |

## How It Works

1.  **The Break (`'`)**: The single quote closes the string for the 'Gifts' category.
2.  **The Tautology (`OR 1=1`)**: This is the heart of the exploit. In Boolean logic, `1=1` is always true. Because we use the `OR` operator, the database engine thinks: *"Show me products where the category is Gifts OR where 1 equals 1."* Since 1 always equals 1, it returns every single row in the table.
3.  **The Comment (`--`)**: This tells the database to ignore the rest of the original query (the part that says `AND released = 1`). This removes the restriction that only "released" products should be shown.

### Visual Representation of the Query Transformation

*   **Original:** `SELECT * FROM products WHERE category = 'Gifts' AND released = 1`
*   **Injected:** `SELECT * FROM products WHERE category = 'Gifts' OR 1=1--' AND released = 1`
*   **How the DB Sees it:** `SELECT * FROM products WHERE category = 'Gifts' OR 1=1`

## Result
As shown in the project documentation (referencing `image_58b701.jpg`), the application displays all products, including those that were unreleased or hidden from the public view.

---




proof of concept 

![sql lab3](sql01.PNG)
