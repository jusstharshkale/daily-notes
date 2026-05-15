Date : 08-05-2026

# Topic - Http deep dive
What is HTTP?
HTTP (HyperText Transfer Protocol) is the communication protocol used between clients (browser/tools) and servers on the web.
-Works on request → response model
-Stateless protocol
-Common ports:
HTTP → 80
HTTPS → 443

HTTP Request Structure :
GET /index.html HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0
Accept: */*

Http Response Structure :
HTTP/1.1 200 OK
Server: nginx
Content-Type: text/html
<html>...</html>

HTTP Methods :
HTTP methods define the action that the client wants to perform on a resource on the server. They are an essential part of web communication and are used in APIs, browsers, and web applications.

GET - The GET method is used to retrieve data from the server.
POST-The POST method is used to send data to the server, usually to create a new resource.
PUT-The PUT method is used to completely update or replace an existing resource.
DELETE-The DELETE method removes a resource from the server.

Http Headers :
| Header                        | Purpose                     | Example                                       |
| ----------------------------- | --------------------------- | --------------------------------------------- |
| `Host`                        | Target domain               | `Host: example.com`                           |
| `User-Agent`                  | Identifies client/browser   | `User-Agent: Mozilla/5.0`                     |
| `Accept`                      | Acceptable response type    | `Accept: application/json`                    |
| `Authorization`               | Authentication credentials  | `Authorization: Bearer TOKEN`                 |
| `Cookie`                      | Sends session cookies       | `Cookie: sessionid=abc123`                    |
| `Referer`                     | Previous page URL           | `Referer: https://google.com`                 |
| `Origin`                      | Request origin              | `Origin: https://example.com`                 |
| `Content-Type`                | Body data format            | `Content-Type: application/json`              |
| `Content-Length`              | Body size                   | `Content-Length: 348`                         |
| `Cache-Control`               | Cache behavior              | `Cache-Control: no-cache`                     |
| `Server`                      | Server software info        | `Server: nginx`                               |
| `Set-Cookie`                  | Sets browser cookies        | `Set-Cookie: sessionid=abc123`                |
| `Location`                    | Redirect URL                | `Location: /login`                            |
| `Access-Control-Allow-Origin` | Allowed CORS origins        | `Access-Control-Allow-Origin: *`              |
| `Strict-Transport-Security`   | Forces HTTPS                | `Strict-Transport-Security: max-age=31536000` |
| `X-Frame-Options`             | Prevents clickjacking       | `X-Frame-Options: DENY`                       |
| `X-Content-Type-Options`      | Prevents MIME sniffing      | `X-Content-Type-Options: nosniff`             |
| `Content-Security-Policy`     | Prevents XSS/resource abuse | `Content-Security-Policy: default-src 'self'` |

# Topic - Working with gobuster
Gobuster is a fast directory/file, DNS, virtual host, and S3 bucket brute-forcing tool written in Go.

Gobuster Modes

Gobuster has 4 major modes:
1.dir → Directory/File Bruteforce - gobuster dir -u http://example.com -w wordlist.txt
2.dns → DNS Subdomain Bruteforce - gobuster dns -d example.com -w subdomains.txt
3.vhost → Virtual Host Bruteforce - gobuster vhost -u http://example.com -w wordlist.txt
4.s3 → AWS S3 Bucket Enumeration - gobuster s3 -w buckets.txt

