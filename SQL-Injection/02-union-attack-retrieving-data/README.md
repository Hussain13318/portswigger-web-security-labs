# SQL Injection UNION Attack: Retrieve Data from Other Tables

- **Platform:** PortSwigger Web Security Academy
- **Difficulty:** Practitioner
- **Category:** SQL Injection / UNION-based SQL injection
- **Lab:** [SQL injection UNION attack, retrieving data from other tables](https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables)
- **Status:** Solved

## Objective

The goal was to use a UNION-based SQL injection to retrieve usernames and passwords from a different database table, then log in as the administrator.

## Tools

- Burp Suite Community Edition
- Web browser
- PortSwigger lab environment

## Steps I Followed

1. I intercepted the product category filter request and sent it to Burp Suite Repeater.
2. I used a UNION SELECT test to identify the number of columns in the original query.
3. I confirmed that the query had two columns and that both columns could display text.
4. I used a UNION SELECT statement to request the `username` and `password` fields from the `users` table.
5. The response showed account details, including the administrator account.
6. I used the administrator credentials in the lab's **My account** login page. The lab was then marked **Solved**.

## Payloads Used

Column and text compatibility test:

```sql
' UNION SELECT 'abc','def'--
```

Retrieve usernames and passwords:

```sql
' UNION SELECT username,password FROM users--
```

## Result

The response exposed usernames and passwords from the lab database. Logging in through the lab as the administrator completed the challenge.

**Security note:** Actual passwords, session cookies, and other authentication values are intentionally not included in this public write-up.

## What I Learned

I learned how UNION-based SQL injection can be used to retrieve data from another table. I also practiced finding the correct column count and checking whether the selected columns accept text.

## Evidence

Add a screenshot showing the lab's **Solved** status. Redact cookies, passwords, and any other authentication details before uploading.
