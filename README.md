# Web Application Hacking List
A list of web application checks sorted by functionality

- [Web Applications](#web-applications)
  - [Categories](#categories)
    - [Signup/Register Form](#signupregister-form)
    - [Login Forms](#login-forms)
    - [Forgotten Password Form](#forgotten-password-form)
    - [Contact Forms](#contact-forms)
    - [Emails Forms](#emails-forms)
  - [Nuances](#nuances)
    - [PHP](#php)
    - [ASP.NET](#aspnet)
    - [JSP](#jsp)


# Web Applications

## Categories

### Signup/Register Form

- Username reusability

### Login Forms

- Authentication Bypass
    - Database Injection 
        - NoSQL
        - MySQL
        - Postgresql
        - etc
    - Maybe Forced Browsing (? TODO)
        - Discovering content that isn't properly protected by the authentication mechanism

### Forgotten Password Form

- Insecure Direct Object References in the password reset link

**Example**
```
http://example.com/password_reset/id/1234
```

- Expiration of the password reset link

- Host header injection for malicious host

**Example**
```
POST http://www.example.com/password_reset/id/1234 HTTP/1.1
Host: yoursite.com
```    
*Reference: https://hackerone.com/reports/281575*
*Reference: https://lightningsecurity.io/blog/host-header-injection/*

- Parameter Pollution to reset multiple accounts
    - If you don't own the account you are trying to reset the password for, it may be possible to achieve this by performing a parameter pollution attack. 

*Reference: https://hackerone.com/reports/322985*

- Check if the email address is tied to the request

**Example**
```

```
*Reference: https://hackerone.com/reports/315879*

- Check for cross-account usage of password reset token

**Example**
1. Reset the password for an account you control
2. Reset the password for a second account you control
3. Attempt to swap the token from one account reset link to another
4. If it works then you may be able to takeover the account

*Reference: [BugBounty How I was Able to Compromise Any User Account via Password Reset Functionality](https://medium.com/bugbountywriteup/bugbounty-how-i-was-able-to-compromise-any-user-account-via-reset-password-functionality-a11bb5f863b3 "BugBounty How I was Able to Compromise Any User Account via Password Reset Functionality")*


### Contact Forms

- Header Injection 
    - Host Header
    - CRLF Injection (CC; BCC)

- Blind Cross-Site Scripting (XSS)
    - XSS Hunter
    - Burp Collaborator
    - Apache Logs
    - etc

- Cross-Site Scripting (XSS)
    - In message preview
    - "Thank you for your email, {YOUR_NAME}"

- Template Injections
    - This may be a lot easier to prove if the form has a "Send copy to my email" feature.

- File Uploads
    - Remote Code Execution
    - Path Traversal
    - Stored XSS
    - Command Injection
    - eXternal XML Entities (XXE)

- Command Injection
    - "test@test.com; ping ip"

### Emails Forms

- Check for Template Injections


## Nuances 

### PHP

- Make sure that all validity checks are strict (`===` vs `==`)

### ASP.NET

### JSP
