Date : 09-05/2026

# Topic - Understanding cookies , sessions , tokens , login workflow , Proxy Workflow
What is Authentication?
Authentication means verifying who the user is.
Example:
User enters:
-Email
-Password
-Server checks credentials
-If correct → user is authenticated

What are Cookies?
A cookie is a small piece of data stored in the browser by a website.The server sends cookies to the browser using HTTP headers.
Example:
Set-Cookie: sessionId=abc123

Types of Cookies :
1. Session Cookie
-Temporary
-Deleted when browser closes
2. Persistent Cookie
-Stored for a fixed time
-Survives browser restart

What is a Session?
A session is server-side storage of user login state.
Instead of storing user data in browser:
-Browser stores only a session ID
-Actual user data lives on server

Session workflow :
1. Login
2. Server verifies user
3. Server Sends Session ID in Cookie
4. Browser Sends Cookie Automatically

What are Tokens?
A token is a piece of data used to verify identity.
Unlike sessions:
-Tokens are usually stored client-side
-Server may not store anything
Most common token:
-JWT (JSON Web Token)

Token-Based Authentication Workflow :
1. User login
2. Server validates user
3. Server sends token
4. Client stores token
5. Client Sends Token
6. Server verifies token

Login Workflow :
1. User submits login form
2. Server validates credentials
3. Server creates session
4. Session ID stored in DB/Redis
5. Session ID sent as cookie
6. Browser stores cookie
7. Browser sends cookie on every request
8. Server validates session ID
9. User stays logged in

Proxy workflow : 
Client Request
      |
      v
Proxy Server
      |
      v
Backend Server
      |
      v
Proxy Server
      |
      v
Client Response

# Topic - Working with Burpsuite
What is Burp Suite?
Burp Suite is a web security testing tool used for:

-Intercepting HTTP/HTTPS traffic
-Modifying requests/responses
-Finding vulnerabilities
-API testing
-Web penetration testing
-Developed by PortSwigger

Components of BurpSuite :
| Tool      | Purpose                    |
| --------- | -------------------------- |
| Proxy     | Intercept requests         |
| Repeater  | Modify and resend requests |
| Intruder  | Automated attacks/fuzzing  |
| Decoder   | Encode/decode data         |
| Comparer  | Compare requests/responses |
| Sequencer | Analyze randomness         |
| Extender  | Add extensions/plugins     |

Burpsuite Workflow : 
Browser
   |
   v
Burp Proxy
   |
   v
Target Website
