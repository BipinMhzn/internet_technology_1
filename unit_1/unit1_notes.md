# Unit 1: Introduction to Web Technology

## 1.1 Web Basics

### 1.1.1 Internet, Intranet, and WWW

#### Internet
- The **Internet** is a global network of interconnected computers and computer networks that communicate using standardized protocols (TCP/IP).
- It is a massive, worldwide network infrastructure connecting millions of private, public, academic, business, and government networks.
- Key characteristics:
  - **Global reach**: Accessible worldwide
  - **Decentralized**: No single controlling authority
  - **Open architecture**: Based on open standards and protocols
  - **Diverse services**: Email, file transfer, remote login, web browsing, streaming, etc.

#### Intranet
- An **Intranet** is a private network accessible only to an organization's members, employees, or authorized users.
- It uses Internet technologies (TCP/IP, HTTP) but operates within a restricted environment.
- Key characteristics:
  - **Private and secure**: Protected by firewalls and security measures
  - **Limited access**: Only authorized users can access
  - **Internal communication**: Used for sharing company information, documents, and resources
  - **Examples**: Company portals, internal websites, employee directories

#### World Wide Web (WWW)
- The **WWW** or **Web** is an information system where documents and resources are identified by URLs and interlinked by hyperlinks.
- It is accessed via the Internet using web browsers.
- Key characteristics:
  - **Service on the Internet**: The Web runs on top of the Internet
  - **Hypertext system**: Documents are linked through hyperlinks
  - **Uses HTTP/HTTPS**: Protocol for transferring web pages
  - **Accessed via browsers**: Chrome, Firefox, Safari, Edge, etc.
  - **Multimedia content**: Text, images, videos, audio, animations

**Key Differences:**
| Aspect | Internet | Intranet | WWW |
|--------|----------|----------|-----|
| Scope | Global network | Private network | Information system |
| Access | Public | Restricted | Public (via Internet) |
| Purpose | Infrastructure | Internal communication | Information sharing |
| Example | Network of networks | Company network | Websites and web pages |

---

### 1.1.2 Static and Dynamic Web Pages

#### Static Web Pages
- **Static web pages** display the same content every time they are accessed.
- Content is fixed and does not change unless manually updated by the developer.

**Characteristics:**
- Written in **HTML, CSS** (and sometimes basic JavaScript)
- Content is **hardcoded** in the HTML file
- **Fast loading** time
- **Easy to create** and host
- **No database** interaction
- **Low cost** to develop and maintain

**Advantages:**
- Quick to develop
- Faster page load times
- Better for SEO (Search Engine Optimization)
- Lower hosting costs
- More secure (no database vulnerabilities)

**Disadvantages:**
- Difficult to update content frequently
- Not suitable for user interaction
- Each page must be created separately
- Limited functionality

**Use Cases:**
- Portfolio websites
- Company brochures
- Landing pages
- Informational websites

#### Dynamic Web Pages
- **Dynamic web pages** generate content dynamically based on user interactions, database queries, or other factors.
- Content can change without manual intervention by developers.

**Characteristics:**
- Use **server-side scripting** languages (PHP, Python, Node.js, Java, etc.)
- Interact with **databases** (MySQL, MongoDB, PostgreSQL)
- Generate **personalized content** for each user
- Support **user authentication** and sessions
- More **complex** to develop

**Advantages:**
- Easy content management
- Highly interactive and personalized
- User-generated content support
- Real-time updates
- Scalable for large websites

**Disadvantages:**
- Slower page load times
- More expensive to develop
- Requires database management
- Security vulnerabilities if not properly coded
- Higher hosting costs

**Use Cases:**
- E-commerce websites
- Social media platforms
- Content Management Systems (CMS)
- Web applications
- User dashboards

---

### 1.1.3 Web Clients

A **web client** is a software application that accesses web services from a server.

#### Types of Web Clients:

**1. Web Browsers:**
- **Definition**: Software applications used to access and display web pages
- **Examples**:
  - Google Chrome
  - Mozilla Firefox
  - Safari
  - Microsoft Edge
  - Opera

**2. Mobile Applications:**
- Apps that access web services via APIs
- Examples: Mobile banking apps, social media apps

**3. Command-line Tools:**
- Tools like `curl`, `wget` for fetching web resources
- Used for testing and automation

#### Functions of Web Clients:
- **Send HTTP requests** to web servers
- **Receive and render** HTML, CSS, and JavaScript
- **Execute client-side scripts** (JavaScript)
- **Store cookies and cache** for faster access
- **Handle user interactions** (clicks, form submissions)
- **Display multimedia content** (images, videos, audio)

---

### 1.1.4 Web Servers

A **web server** is a software (and hardware) that stores, processes, and delivers web pages to clients.

#### Popular Web Servers:
- **Apache HTTP Server** (Apache)
- **Nginx**
- **Microsoft Internet Information Services (IIS)**
- **LiteSpeed**
- **Node.js** (JavaScript runtime used as a web server)

#### Functions of Web Servers:
- **Store web content**: HTML files, images, CSS, JavaScript, etc.
- **Process HTTP requests**: Receive and interpret client requests
- **Execute server-side scripts**: PHP, Python, Node.js, etc.
- **Send HTTP responses**: Deliver requested resources to clients
- **Manage security**: SSL/TLS certificates, authentication
- **Log activities**: Track requests, errors, and access patterns
- **Load balancing**: Distribute traffic across multiple servers

#### How Web Servers Work:
1. Client sends an HTTP request to the server
2. Server receives and processes the request
3. Server executes any necessary server-side scripts
4. Server retrieves requested resources (files, database data)
5. Server sends an HTTP response back to the client
6. Client renders the response in the browser

---

## 1.2 Client-Server Architecture

The **client-server architecture** is a computing model where clients request services and servers provide those services.

### 1.2.1 Single Tier Architecture

- Also known as **monolithic architecture**
- All components (presentation, business logic, data storage) reside on a **single machine**
- No separation between client and server

**Characteristics:**
- **Simple design**
- **Easy to deploy** and manage
- **No network dependency**
- **Limited scalability**
- **Single point of failure**

**Advantages:**
- Easy to develop and test
- Fast performance (no network latency)
- Low cost

**Disadvantages:**
- Not scalable
- Difficult to maintain for large applications
- Security risks (all data on one machine)
- No concurrent access for multiple users

**Examples:**
- Desktop applications (MS Word, Notepad)
- Standalone software

---

### 1.2.2 Two-Tier Architecture

- Also known as **client-server architecture**
- **Two layers**:
  1. **Client tier** (Presentation layer)
  2. **Server tier** (Database layer)

**How it Works:**
- Client directly communicates with the database server
- Business logic is either on the client or database server
- No middle layer

**Characteristics:**
- **Direct communication** between client and database
- **Faster** than three-tier (fewer layers)
- **Limited scalability**
- **Tight coupling** between client and database

**Advantages:**
- Easy to maintain
- Faster response time
- Suitable for small to medium applications

**Disadvantages:**
- Poor scalability
- Security concerns (direct database access)
- Performance issues with many clients
- Hard to modify business logic

**Examples:**
- Railway reservation systems
- Library management systems
- Contact management systems

---

### 1.2.3 Multi-Tier Architecture (Three-Tier)

- Most common architecture for web applications
- **Three layers**:
  1. **Presentation tier** (Client/UI layer)
  2. **Application tier** (Business logic/middleware layer)
  3. **Data tier** (Database layer)

**How it Works:**
- Client interacts only with the presentation layer
- Application server handles business logic
- Database server manages data storage
- Each layer is independent and can be updated separately

**Characteristics:**
- **Separation of concerns**
- **High scalability**
- **Better security** (no direct database access)
- **Flexible and maintainable**
- **Load distribution** across multiple servers

**Advantages:**
- Highly scalable
- Better security
- Easy to maintain and update
- Reusable components
- Supports multiple client types

**Disadvantages:**
- More complex to develop
- Higher cost
- Slower than two-tier (more network hops)

**Examples:**
- E-commerce websites (Amazon, eBay)
- Banking applications
- Social media platforms
- Enterprise applications

**N-Tier Architecture:**
- Extension of three-tier with additional layers
- Examples: Microservices, service-oriented architecture

---

## 1.3 HTTP: HTTP Request and Response

**HTTP (HyperText Transfer Protocol)** is an application-layer protocol for transmitting hypermedia documents (HTML).

### HTTP Request

An HTTP request is sent by a client to a server to request a resource.

**Components of an HTTP Request:**

1. **Request Line:**
   - Method (GET, POST, PUT, DELETE, etc.)
   - URL/URI (the resource being requested)
   - HTTP version (HTTP/1.1, HTTP/2)

   Example: `GET /index.html HTTP/1.1`

2. **Headers:**
   - Metadata about the request
   - Examples:
     - `Host: www.example.com`
     - `User-Agent: Mozilla/5.0`
     - `Accept: text/html`
     - `Content-Type: application/json`

3. **Body (Optional):**
   - Data sent with the request (for POST, PUT)
   - Examples: Form data, JSON payload

**Common HTTP Methods:**
- **GET**: Retrieve data from the server
- **POST**: Submit data to the server (e.g., form submission)
- **PUT**: Update existing data on the server
- **DELETE**: Remove data from the server
- **HEAD**: Similar to GET but retrieves only headers
- **OPTIONS**: Describe communication options
- **PATCH**: Partial modification of a resource

**Example HTTP Request:**
```
GET /api/users/123 HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0
Accept: application/json
Connection: keep-alive
```

---

### HTTP Response

An HTTP response is sent by a server back to the client after processing the request.

**Components of an HTTP Response:**

1. **Status Line:**
   - HTTP version
   - Status code
   - Status message

   Example: `HTTP/1.1 200 OK`

2. **Headers:**
   - Metadata about the response
   - Examples:
     - `Content-Type: text/html`
     - `Content-Length: 1234`
     - `Server: Apache/2.4.41`
     - `Set-Cookie: sessionId=abc123`

3. **Body:**
   - The actual content (HTML, JSON, XML, image, etc.)

**Common HTTP Status Codes:**

**1xx - Informational:**
- `100 Continue`

**2xx - Success:**
- `200 OK` - Request successful
- `201 Created` - Resource created successfully
- `204 No Content` - Request successful, no content to return

**3xx - Redirection:**
- `301 Moved Permanently` - Resource moved to a new URL
- `302 Found` - Temporary redirect
- `304 Not Modified` - Cached version is still valid

**4xx - Client Errors:**
- `400 Bad Request` - Invalid request syntax
- `401 Unauthorized` - Authentication required
- `403 Forbidden` - Server refuses to authorize
- `404 Not Found` - Resource not found
- `405 Method Not Allowed` - HTTP method not supported

**5xx - Server Errors:**
- `500 Internal Server Error` - Generic server error
- `502 Bad Gateway` - Invalid response from upstream server
- `503 Service Unavailable` - Server temporarily unavailable
- `504 Gateway Timeout` - Upstream server timeout

**Example HTTP Response:**
```
HTTP/1.1 200 OK
Date: Sun, 19 Jan 2026 10:00:00 GMT
Server: Apache/2.4.41
Content-Type: text/html; charset=UTF-8
Content-Length: 1234

<!DOCTYPE html>
<html>
<head>
    <title>Example Page</title>
</head>
<body>
    <h1>Hello World!</h1>
</body>
</html>
```

---

## 1.4 URL (Uniform Resource Locator)

A **URL** is the address used to access resources on the web.

### Structure of a URL:

```
scheme://username:password@host:port/path?query#fragment
```

**Components:**

1. **Scheme/Protocol:**
   - Indicates the protocol to use
   - Examples: `http`, `https`, `ftp`, `file`
   - Example: `https://`

2. **Username and Password (Optional):**
   - Credentials for authentication
   - Rarely used in modern web
   - Example: `user:pass@`

3. **Host:**
   - Domain name or IP address
   - Examples: `www.google.com`, `192.168.1.1`

4. **Port (Optional):**
   - Specifies the port number
   - Default: 80 for HTTP, 443 for HTTPS
   - Example: `:8080`

5. **Path:**
   - Location of the resource on the server
   - Example: `/products/electronics`

6. **Query String (Optional):**
   - Parameters passed to the server
   - Starts with `?`
   - Multiple parameters separated by `&`
   - Example: `?id=123&category=books`

7. **Fragment (Optional):**
   - Identifies a specific section within a page
   - Starts with `#`
   - Example: `#section2`

### Examples:

```
https://www.example.com/products/laptop?id=123&color=black#reviews
```
- **Scheme**: https
- **Host**: www.example.com
- **Path**: /products/laptop
- **Query**: ?id=123&color=black
- **Fragment**: #reviews

```
http://localhost:8080/api/users
```
- **Scheme**: http
- **Host**: localhost
- **Port**: 8080
- **Path**: /api/users

### URL Encoding:
- Special characters must be encoded
- Spaces become `%20` or `+`
- Examples:
  - `hello world` → `hello%20world`
  - `user@email.com` → `user%40email.com`

---

## 1.5 Client-Side Scripting

**Client-side scripting** refers to scripts that run in the user's browser (client) rather than on the server.

### Characteristics:
- Executes on the **client's machine**
- **Reduces server load**
- Provides **immediate feedback** to users
- Can work **offline** (after initial load)
- **Visible to users** (can view source code)

### Primary Language: JavaScript

**JavaScript** is the most common client-side scripting language.

### Features of Client-Side Scripting:
- **DOM manipulation**: Change HTML content dynamically
- **Event handling**: Respond to user actions (clicks, key presses)
- **Form validation**: Validate user input before submission
- **Animations**: Create visual effects and transitions
- **AJAX**: Asynchronous communication with server
- **Local storage**: Store data in the browser
- **Dynamic content**: Update page without reloading

### Advantages:
- **Fast response**: No server round-trip needed
- **Reduced server load**: Processing done on client
- **Better user experience**: Immediate feedback
- **Interactive interfaces**: Rich user interactions
- **Works offline**: Can function without internet (after loading)

### Disadvantages:
- **Security risks**: Code is visible and can be manipulated
- **Browser compatibility**: May work differently across browsers
- **Disabled by users**: Users can disable JavaScript
- **Limited access**: Cannot access server-side resources directly
- **Performance**: Depends on client's device capabilities

### Common Uses:
- Form validation
- Image sliders and carousels
- Modal popups
- Dropdown menus
- Auto-complete suggestions
- Real-time calculations
- Interactive maps
- Single Page Applications (SPAs)

### Technologies:
- **JavaScript** (vanilla, ES6+)
- **Frameworks/Libraries**:
  - React
  - Vue.js
  - Angular
  - jQuery (older, still used)

---

## 1.6 Server-Side Scripting

**Server-side scripting** refers to scripts that run on the web server before sending the response to the client.

### Characteristics:
- Executes on the **server**
- **Secure**: Code is not visible to users
- **Database access**: Can interact with databases
- **Session management**: Handle user sessions
- **More processing power**: Leverages server resources

### Common Server-Side Languages:
- **PHP**: Popular for web development (WordPress, Laravel)
- **Python**: Flask, Django frameworks
- **Node.js**: JavaScript on the server
- **Java**: JSP, Servlets, Spring
- **Ruby**: Ruby on Rails
- **C#**: ASP.NET
- **Go**: Modern, fast language

### Features of Server-Side Scripting:
- **Database operations**: CRUD operations (Create, Read, Update, Delete)
- **User authentication**: Login, registration, sessions
- **Dynamic content generation**: Generate HTML based on data
- **File operations**: Read, write, upload files
- **Email sending**: Send emails from the server
- **Payment processing**: Handle secure transactions
- **API creation**: Build RESTful APIs

### Advantages:
- **Secure**: Code is hidden from users
- **Powerful**: Access to server resources and databases
- **Consistent**: Works regardless of client's browser
- **Centralized**: Logic maintained in one place
- **Data processing**: Handle complex calculations and operations

### Disadvantages:
- **Server load**: All processing on the server
- **Slower response**: Requires server round-trip
- **Scalability**: May need more servers for high traffic
- **Cost**: Requires server resources

### Common Uses:
- User authentication and authorization
- Database operations
- Content Management Systems (CMS)
- E-commerce shopping carts
- Payment processing
- Email sending
- File uploads
- API backends

### Request Flow:
1. Client sends request to server
2. Server executes server-side script
3. Script processes data, queries database
4. Server generates HTML/JSON response
5. Response sent back to client

### Example Scenario:
**User Login Process:**
1. User enters username/password (client-side)
2. Form submitted to server
3. Server-side script validates credentials
4. Script checks database for user
5. Creates session if valid
6. Sends response back to client

---

## 1.7 Web 1.0, Web 2.0, and Web 3.0

The evolution of the web through different generations:

### Web 1.0 (1991-2004) - The "Read-Only" Web

**Characteristics:**
- **Static web pages**: Content rarely changed
- **One-way communication**: Information flows from website to user
- **Limited interactivity**: Minimal user engagement
- **HTML-based**: Simple websites with basic formatting
- **No user-generated content**
- **Slow internet**: Dial-up connections

**Features:**
- Static HTML pages
- Basic forms
- Email
- Online directories
- Personal websites
- Company brochures online

**Examples:**
- Early Yahoo directory
- Netscape Navigator
- Static corporate websites
- Basic online catalogs

**Limitations:**
- No user interaction
- Difficult to update content
- Limited multimedia
- Slow loading times
- No social features

**Metaphor**: Web 1.0 is like a library - you can read information but not contribute or interact.

---

### Web 2.0 (2004-Present) - The "Read-Write" Web

**Characteristics:**
- **Dynamic content**: Websites update frequently
- **User-generated content**: Users create and share content
- **Social interaction**: Comments, likes, shares
- **Rich user experience**: AJAX, APIs, multimedia
- **Collaboration**: Wikis, forums, social networks
- **Mobile-friendly**: Responsive design

**Key Technologies:**
- AJAX (Asynchronous JavaScript and XML)
- REST APIs
- JavaScript frameworks (React, Angular, Vue)
- RSS feeds
- Cloud computing
- Mobile applications

**Features:**
- Social media platforms
- Blogs and vlogs
- Wikis (Wikipedia)
- Video sharing (YouTube)
- Photo sharing (Instagram)
- Podcasts
- Web applications
- Collaborative tools (Google Docs)

**Examples:**
- Facebook, Twitter, Instagram
- YouTube
- Wikipedia
- WordPress, Medium
- Google Maps
- Gmail, Outlook Web
- Dropbox, Google Drive
- Online shopping (Amazon)

**Advantages:**
- User participation
- Rich interactive experiences
- Real-time updates
- Personalized content
- Social connectivity
- Platform independence

**Metaphor**: Web 2.0 is like a conversation - users both consume and create content, interact with each other.

---

### Web 3.0 (Emerging) - The "Semantic Web" or "Decentralized Web"

**Characteristics:**
- **Decentralized**: No central authority or control
- **Blockchain-based**: Distributed ledger technology
- **Semantic web**: Machines understand content meaning
- **AI-powered**: Artificial intelligence and machine learning
- **User ownership**: Users own their data and digital assets
- **Trustless**: No need for intermediaries
- **Privacy-focused**: Enhanced user privacy

**Key Technologies:**
- **Blockchain**: Decentralized data storage
- **Cryptocurrency**: Digital currencies (Bitcoin, Ethereum)
- **NFTs**: Non-fungible tokens (digital ownership)
- **Smart contracts**: Self-executing contracts
- **Distributed storage**: IPFS, Filecoin
- **Decentralized identity**: Self-sovereign identity
- **AI and ML**: Natural language processing, personalization

**Features:**
- Decentralized applications (DApps)
- Cryptocurrency wallets
- NFT marketplaces
- Decentralized finance (DeFi)
- Semantic search
- AI assistants
- 3D/VR experiences (Metaverse)
- Edge computing

**Examples:**
- Ethereum blockchain
- Bitcoin
- IPFS (InterPlanetary File System)
- OpenSea (NFT marketplace)
- Brave browser
- Decentraland (virtual world)
- ChatGPT and AI assistants
- Web3 wallets (MetaMask)

**Goals:**
- User data ownership
- Privacy and security
- Eliminate intermediaries
- Transparent transactions
- Censorship resistance
- Better AI understanding

**Advantages:**
- Data ownership by users
- Enhanced privacy
- No single point of failure
- Transparency
- Reduced censorship
- Direct peer-to-peer transactions

**Challenges:**
- Complexity
- Scalability issues
- High energy consumption
- Regulatory uncertainty
- Steep learning curve
- Limited adoption

**Metaphor**: Web 3.0 is like a decentralized marketplace - users own their data, control their identity, and transact directly without intermediaries.

---

## Summary Comparison

| Feature | Web 1.0 | Web 2.0 | Web 3.0 |
|---------|---------|---------|---------|
| **Period** | 1991-2004 | 2004-Present | Emerging |
| **Content** | Static | Dynamic | Intelligent |
| **User Role** | Read-only | Read-Write | Read-Write-Own |
| **Interaction** | Minimal | High | AI-powered |
| **Data Storage** | Centralized | Centralized | Decentralized |
| **Technology** | HTML | AJAX, APIs | Blockchain, AI |
| **Examples** | Static sites | Social media | Crypto, NFTs |
| **Focus** | Information | Participation | Decentralization |

---

## Key Takeaways

1. **Web Basics**: Understanding the difference between Internet (infrastructure), Intranet (private network), and WWW (information system)

2. **Static vs Dynamic**: Static pages are fixed, dynamic pages are generated on-the-fly based on user interactions and data

3. **Client-Server**: Web clients (browsers) request resources from web servers, which process and deliver responses

4. **Architecture**: Evolution from single-tier (monolithic) to multi-tier (separated concerns) for better scalability and maintenance

5. **HTTP Protocol**: Foundation of web communication with request-response model and standardized status codes

6. **URL Structure**: Systematic way to locate and access resources on the web

7. **Scripting**: Client-side (browser) for interactivity, server-side (server) for data processing and security

8. **Web Evolution**: From static read-only (Web 1.0), to interactive social (Web 2.0), to decentralized semantic (Web 3.0)

---

## Study Questions

1. What is the difference between the Internet and the World Wide Web?
2. Compare static and dynamic web pages with examples.
3. Explain the three-tier client-server architecture.
4. What are the main components of an HTTP request and response?
5. Describe the structure of a URL with an example.
6. What are the advantages and disadvantages of client-side scripting?
7. How does server-side scripting differ from client-side scripting?
8. Explain the evolution from Web 1.0 to Web 3.0.
9. What are the common HTTP status codes and their meanings?
10. Why is multi-tier architecture preferred over two-tier for web applications?