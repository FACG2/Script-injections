# Script injections / safety issues 

**Code injection** is the exploitation of a computer bug that is caused by processing invalid data. Injection is used by an attacker to introduce (or "inject") code into a vulnerable computer program and change the course of execution. The result of successful code injection can be disastrous, for example by allowing computer worms to propagate.

### Two Code injections :
* Cross-site scripting (XSS) – client side
is a type of computer security vulnerability typically found in web applications. XSS enables attackers to inject client-side scripts into web pagesviewed by other users. 

* Script Injection – server side
Injection can result in data loss or corruption, lack of accountability, or denial of access. Injection can sometimes lead to complete host takeover.


### Preventing code injection:
Using APIs that, if used properly, are secure against all input characters. Parameterized queries (also known as "Compiled queries", "prepared statements", "bound variables") allows for moving user data out of string to be interpreted.
* Enforcing language separation via a static type system.
* Input validation, such as whitelisting for inputs
* Output encoding, i.e. preventing HTML Injection (XSS) attacks against web site visitors
HttpOnly is a flag for HTTP Cookies that, when set, does not allow client-side script interaction with cookies, thereby preventing certain XSS attacks.
* Modular shell disassociation from kernel With SQL Injection, one can use parameterized queries, stored procedures, whitelist input validation, and more to help mitigate Code Injection problems.

#### Example :

[Try inject website :](http://www.techpanda.org/dashboard.php)


let assume that this is a log in page for admin dashboard, it will only open the dashboard when you access the right email and password,
- try access it with random email and password
- lets try adding any email and then add this password = xxx') OR 1 = 1 -- ]
Click on Submit button
You will be directed to the dashboard

The generated SQL statement will be as follows

`SELECT * FROM users WHERE email = 'xxx@xxx.xxx' AND password = md5('xxx') OR 1 = 1 -- ]');`

> **1=1** will be **True**

`Select * From users where True AND TRUE `


To prevent the injection we can encode the input password before sending it to the query handling
```js
use : var res = encodeURI(password);
```
and the res will be encoded , so you save and get encoded password from the database
We can use other ways like the npm libraries below:  
```
npm Validator
A library of string validators and sanitizers.
XSS
security-filters
```
### Resourse:
- [Wikipedia](https://en.wikipedia.org/wiki/SQL_injection)
- [SQL Injection Cheat Sheet](https://www.veracode.com/security/sql-injection)
