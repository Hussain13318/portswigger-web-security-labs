# PortSwigger Web Security Academy Labs

This repository contains my hands-on practice and solutions for selected labs from [PortSwigger Web Security Academy](https://portswigger.net/web-security).

I use these labs to understand common web application vulnerabilities, test them in a controlled environment, and document the steps and lessons from each exercise.

## Completed Labs

| # | Lab | Category | Difficulty | Status |
|---|---|---|---|---|
| 01 | [SQL injection vulnerability in WHERE clause allowing retrieval of hidden data](SQL-Injection/01-where-clause-hidden-data/README.md) | SQL Injection | Apprentice | Solved |
| 02 | [SQL injection UNION attack, retrieving data from other tables](SQL-Injection/02-union-attack-retrieving-data/README.md) | SQL Injection | Practitioner | Solved |
| 03 | [Exploiting XXE to retrieve data by repurposing a local DTD](XXE/03-repurposing-local-dtd/README.md) | XXE | Expert | Solved |

## Tools Used

- Burp Suite Community Edition
- Web browser
- PortSwigger Web Security Academy

## Topics Practiced

- SQL injection in a product category filter
- UNION-based SQL injection
- Retrieving data from another database table
- XML External Entity (XXE)
- Blind XXE using error messages
- Repurposing a local DTD

## Repository Structure

- `SQL-Injection/` contains the two SQL injection lab write-ups.
- `XXE/` contains the XXE lab write-up.
- Each lab folder has its own `README.md` and an `evidence/` folder for safe, redacted screenshots.

## Disclaimer

All testing described here was performed in PortSwigger Web Security Academy's intentionally vulnerable lab environments for educational purposes. These techniques should only be tested on systems where you have permission.

## About This Repository

This is a learning record and will be updated as I complete more labs.
