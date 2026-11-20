# SQL Injection: Retrieve Hidden Data from a WHERE Clause

- **Platform:** PortSwigger Web Security Academy
- **Difficulty:** Apprentice
- **Category:** SQL Injection
- **Lab:** [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](https://portswigger.net/web-security/sql-injection/lab-retrieve-hidden-data)
- **Status:** Solved

## Objective

The goal was to exploit the product category filter so that the application displayed unreleased or hidden products.

## Tools

- Burp Suite Community Edition
- Web browser
- PortSwigger lab environment

## Steps I Followed

1. I opened the lab website and selected a product category.
2. I intercepted the category filter request in Burp Suite and sent it to Repeater.
3. I tested the category parameter by adding a quote and a SQL comment marker to change how the query was interpreted.
4. I then used a condition that is always true to make the database return products beyond the selected category.
5. The page displayed the hidden products, and the lab showed as solved.

## Payloads Used

Initial comment test:

```sql
Gifts'--
```

Condition that always evaluates to true:

```sql
' OR 1=1--
```

## Result

The application returned all products, including products that were meant to remain hidden. The lab was marked **Solved**.

## What I Learned

I learned that user input placed directly into a SQL query can change the query's logic. I also practiced intercepting and modifying requests with Burp Suite Repeater.

## Evidence

Add a screenshot showing the lab's **Solved** status here. Before uploading, make sure the screenshot does not show session cookies or other account information.
