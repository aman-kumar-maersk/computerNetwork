### [Home](/README.md)

# HyperText Transfer Protocol

HTTP is the protocol mainly used for transferring Web Pages and related resources over the Internet. It operates on top of [TCP](/pages/dtp/README.md#1-transmission-control-protocol-tcp) and follows a `Request - Response method.`

#### Following are some of the features of [HTTP Protocol](/null)

1. #### **[Stateless Protocol](/null)**  
    HTTP is a stateless protocol, which means each request-response cycle is independent and does not remember previous interactions. Servers do not retain client information between requests, making each request self-contained. To maintain state across multiple interactions, techniques like cookies or session management are used to store user-related data.

    ![Stateless Http](/assets/stateless.png)

    ### The Solution ?
    The solution to handle state in a stateless protocol like HTTP is to use techniques such as cookies and session management, etc.

    1. **Cookies:**  
        Cookies are small pieces of data stored on the client-side by the server. They are sent in the HTTP headers with each request and allow the server to identify and remember specific clients. Cookies can store user preferences, session IDs, and other relevant information, enabling stateful interactions between the client and server.

        ![Cookies](/assets/cookies.png)

    2. **Session Management:**  
        When a client initiates a session with a server, a unique session ID is generated and stored on the server-side. The session ID is often sent to the client as a cookie or as a URL parameter. Subsequent requests from the same client include the session ID, allowing the server to retrieve stored session data and maintain state throughout the session.

        Sessions can be saved and managed on the client via Encrypted tokens as well as on the Servers via unique IDs.

        One such example is `JWT (JSON WEB TOKENS)` . They are tokens that contains user data to identify user details and are signed with a secret key to verify authenticity on the server side.
        These are generally passed in the Authroisation Header in an authenticated HTTP request.

        **HTTP Authorisation Header**  
        ```HTTP
        Authorisation: Bearer <JWT Token>
        ```

        ![JWT Authroisation](/assets/jwt.png)

    By utilizing cookies and session management, websites and applications can maintain state and offer personalized experiences to users while working within the stateless nature of the HTTP protocol.

2. #### **[Request Methods (GET, POST, PUT, DELETE, etc.)](/null)**  
    HTTP Request Methods are verbs that indicate the type of action a client wants to perform on a resource. They help specify the intent of the request and are crucial for  various interactions in web applications.



    1. **GET:** Requests data from the server. It is used to retrieve information identified by the URL.

    2. **POST:** Sends data to the server for processing, often used for form submissions and creating new resources.

    3. **PUT:** Updates an existing resource on the server with the data provided in the request.

    4. **DELETE:** Deletes a specified resource on the server.

    5. **PATCH:** Partially updates an existing resource with the data provided in the request.

    6. **HEAD:** Similar to GET, but only returns the headers and not the actual content, useful for checking resource metadata.

    7. **OPTIONS:** Retrieves the HTTP methods and communication options available for the given URL.

    8. **CONNECT:** Establishes a network connection to a server through a proxy.

    9. **TRACE:** Echoes back the received request for diagnostic purposes.

    These request methods enable clients to interact with servers in a meaningful and specific way, allowing for data retrieval, creation, modification, and deletion of resources on the web.


3. [Response Status Codes (200 OK, 404 Not Found, etc.)](/null)  
    [HTTP (Hypertext Transfer Protocol)](./HTTP.md) response status codes are three-digit numbers returned by a web server in response to a client's request made to the server. These codes provide information about the status of the requested resource and the outcome of the request. Here's a brief overview of some common HTTP response status codes:

    1. **1xx - Informational:**
        - **100 Continue**: The server has received the initial part of the request and the client should continue with the request or ignore it if it's already completed.

    2. **2xx - Successful:**
        - **200 OK**: The request was successful, and the server has returned the requested content.
        - **201 Created**: The request has been fulfilled, and a new resource has been created as a result.
        - **204 No Content**: The server successfully processed the request but there's no content to send in the response.

    3. **3xx - Redirection:**
        - **301 Moved Permanently**: The requested resource has been permanently moved to a new location, and the client should update its references.
        - **302 Found (Moved Temporarily)**: Similar to 301, but indicates that the move is temporary.
        - **304 Not Modified**: The client's cached copy is still valid, so the server responds without sending the requested content.

    4. **4xx - Client Errors:**
        - **400 Bad Request**: The server couldn't understand the request due to malformed syntax or other client errors.
        - **401 Unauthorized**: Authentication is required, and the client needs to provide valid credentials.
        - **403 Forbidden**: The client does not have permission to access the requested resource.
        - **404 Not Found**: The requested resource could not be found on the server.

    5. **5xx - Server Errors:**
        - **500 Internal Server Error**: The server encountered an error while processing the request.
        - **502 Bad Gateway**: The server, while acting as a gateway or proxy, received an invalid response from the upstream server.
        - **503 Service Unavailable**: The server is temporarily unable to handle the request (e.g., due to maintenance or overloading).  
  <br>

    | Status Code | Description                    | Example Use Case                  |
    |-------------|--------------------------------|-----------------------------------|
    | 200         | OK                             | Successfully retrieved content    |
    | 404         | Not Found                      | Requested resource not found      |
    | 500         | Internal Server Error          | Server encountered an error       |
    | 302         | Found (Moved Temporarily)      | Temporary redirection             |
    | 401         | Unauthorized                   | Authentication required           |

4. #### **[Headers](/null)**
    HTTP headers are key-value pairs of information sent between a client (usually a web browser) and a server during an HTTP request or response. They provide additional context and instructions for how the request or response should be handled. Here are some common HTTP headers:

    1. **User-Agent**: Specifies the user agent (e.g., browser) making the request.
    2. **Content-Type**: Defines the type of data in the request or response body.
    3. **Authorization**: Used for sending credentials or tokens for authentication.
    4. **Cache-Control**: Controls caching behavior to improve performance.
    5. **Location**: Indicates the new location for redirection.
    6. **Accept**: In a request, specifies the media types that the client can process.
    7. **Server**: In a response, indicates the server software being used.

    Sample of headers :
    #### Request Headers
    ```HTTP
    User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/91.0.4472.164 Safari/537.36
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c
    ```
    #### Response Headers
    ```HTTP
    Content-Type: application/json
    Cache-Control: max-age=3600, public
    Server: Apache/2.4.41 (Unix) OpenSSL/1.1.1g
    ```



5. #### **[Request Body](/null)**

    The request body is the data sent from the client to the server as part of an HTTP request. It contains information that the server needs to process the request, such as form data, JSON payloads, or other content types. The request body is typically used in HTTP methods like POST, PUT, and PATCH to send data to the server for processing or updating.

    1. **Content-Type**: The `Content-Type` [header](#headers) in the request indicates the format or type of data in the request body. Common content types include:
        - `application/json`: Used for sending JSON data.
        - `application/x-www-form-urlencoded`: Used for sending form data.
        - `multipart/form-data`: Used for sending files and form data.

    2. **[Request Methods](#request-methods-get-post-put-delete-etc)**: HTTP methods that commonly use request bodies include:
        - **POST**: Used to submit data to be processed to create a new resource.
        - **PUT**: Used to update a resource, or create it if it doesn't exist.
        - **PATCH**: Used to partially update a resource.
        - etc



    #### FormData Format Request Body

    ```
    name=John%20Doe&email=johndoe%40example.com&age=30
    ```

    #### JSON Request Body

    To create a new user, the client can send a JSON object in the request body with the following properties:

    ```json
    {
        "name": "John Doe",
        "email": "johndoe@example.com",
        "age": 30
    }
    ```

6. #### **[Response Body](/null)**  
    The response body is the data sent from the server back to the client as part of an HTTP response. It contains the actual content requested by the client, which could be HTML, JSON, XML, binary data, or any other format. The response body is typically used to transmit the requested information, such as a web page, API data, or file content.

    **Content-Type**: The `Content-Type` header in the response indicates the format or type of data in the response body. This helps the client understand how to interpret the received data.

    **Status Code**: The HTTP status code in the response indicates the outcome of the request. The status code is not part of the response body but provides context for how the response should be interpreted.

    **Example Response Body in JSON Format**:
    ```json
    {
        "name": "John Doe",
        "email": "johndoe@example.com",
        "age": 30,
    }
    ```

    **Example Response Body in HTML Format**:

    ```html
    <!DOCTYPE html>
        <html>
            <head>
                <title>Welcome to Our Website</title>
            </head>
        <body>
            <h1>Hello, John Doe!</h1>
            <p>Your email is johndoe@example.com, and you are 30 years old.</p>
        </body>
    </html>
    ```

    ### JSON Response Body
    When the client requests user information, the server responds with a JSON object in the response body:

    ```json
    {
        "name": "John Doe",
        "email": "johndoe@example.com",
        "age": 30
    }
    ```

    The client can parse this JSON data to display the user's details on the application.


7. #### **[URL (Uniform Resource Locator)](/null)**  
    A Uniform Resource Locator (URL) is a reference or address used to locate resources on the internet. URLs are used to specify the location of web pages, files, services, and other resources accessible through the internet. A URL typically consists of several components that define how to access the resource. Here's an overview of the components of a URL:

    1. **Scheme**: The scheme indicates the protocol or method used to access the resource. Common schemes include:
        - `http`: Hypertext Transfer Protocol (unencrypted)
        - `https`: Hypertext Transfer Protocol Secure (encrypted)
        - `ftp`: File Transfer Protocol
        - `mailto`: Email addresses

    2. **Domain or Host**: The domain or host specifies the location of the server that hosts the resource. It is represented as a human-readable domain name (e.g., `example.com`) or an IP address (e.g., `192.0.2.1`).

    3. **Port**: Optional. Specifies the port number through which the client communicates with the server. If omitted, the default port for the scheme is used (e.g., `80` for HTTP, `443` for HTTPS).

    4. **Path**: The path specifies the specific location of the resource on the server's filesystem or web application. It starts with a forward slash `/`.

    5. **Query Parameters**: Optional. Used to send data to the server as part of the URL. Parameters are separated by ampersands `&`, and each parameter consists of a key and a value . Eg.
        ```
        ?key1=value1&key2=value2
        ```

    6. **Fragment**: Optional. Represents a specific section or identifier within the resource. It is often used in HTML documents to point to a specific part of the page (e.g., `#section2`).

    7. **Example URL**:
        ```
        https://www.example.com:443/products?id=12345&page=2#section3
        ```

    Snippet illustrating the components of a URL:

    ### URL Components

    A URL consists of the following components:

    - **Scheme**: `https`
    - **Domain**: `www.example.com`
    - **Port**: `443`
    - **Path**: `/products`
    - **Query**: `?id=12345&page=2`
    - **Fragment**: `#section3`

    When combined, they form the complete URL: `https://www.example.com:443/products?id=12345&page=2#section3`.

8. #### **[Cookies](/null)**  
    Cookies are small pieces of data that a web server sends to a user's web browser during a browsing session. These cookies are stored on the user's device and are sent back to the server with each subsequent HTTP request. Cookies are commonly used to track user sessions, store user preferences, and implement features like shopping carts in web applications. A concise overview of cookies:

    ![Cookies](/assets/cookies.png)

    1. **Cookie Creation**: When a user visits a website, the server can send one or more cookies to the user's browser. These cookies are typically created using the `Set-Cookie` header in the HTTP response.

    ```
    Set-Cookie: id=a3fWa; Expires=Thu, 21 Oct 2021 07:28:00 GMT; Secure; HttpOnly
    ```


    2. **Cookie Storage**: Cookies are stored on the user's device, either in memory (session cookies) or on disk (persistent cookies), depending on their attributes. Session cookies are temporary and expire when the browser is closed, while persistent cookies can have set expiration dates.

    3. **Cookie Structure**: A cookie consists of a name, a value, and various attributes. Common attributes include:
        - **Domain**: Specifies which domain can access the cookie.
        - **Path**: Defines the URL path for which the cookie is valid.
        - **Expiration**: Indicates when the cookie should expire.
        - **Secure**: Ensures the cookie is only transmitted over secure (HTTPS) connections.
        - **HttpOnly**: Prevents JavaScript from accessing the cookie.

        ![Cookie Structure](/assets/cookieStructure.png)

    4. **Cookie Usage**: Cookies are often used for various purposes, such as:
        - **Session Management**: Maintaining user sessions and authentication.
        - **User Preferences**: Storing user settings and preferences.
        - **Tracking**: Collecting user behavior data for analytics.
        - **Shopping Carts**: Keeping track of items in an online shopping cart.
        - **Personalization**: Customizing content for users.


    Cookies play a crucial role in web applications, enabling features like user authentication, shopping carts, and personalized experiences.

9. #### **[HTTPS (Hypertext Transfer Protocol Secure)](/null)**
    HTTPS (Hypertext Transfer Protocol Secure) is a secure version of the HTTP protocol used for transmitting data over the internet. It adds a layer of security by encrypting the data exchanged between a user's web browser and a web server. Here's a concise overview of HTTPS:
    ![HttpAndS](/assets/httpAndS.webp)

    1. **Encryption**: HTTPS uses encryption protocols such as SSL (Secure Sockets Layer) or its successor, TLS (Transport Layer Security), to secure the data transmitted between the client and server. This encryption ensures that data cannot be easily intercepted or tampered with by unauthorized parties.

    2. **Authentication**: HTTPS provides a level of authentication, confirming that the user's browser is connected to the intended web server. This helps prevent man-in-the-middle attacks where a malicious party intercepts and impersonates the server.

    3. **Data Integrity**: It ensures the integrity of the data by preventing tampering or modification during transmission.

    4. **Secure Connection**: A secure connection is established using digital certificates, which are issued by trusted Certificate Authorities (CAs). These certificates validate the identity of the server and provide a public key for encrypting data.

    5. **URL Prefix**: HTTPS URLs start with "https://" instead of "http://". This prefix indicates that the connection is secured.

    6. **Benefits**: HTTPS is crucial for protecting sensitive data, such as login credentials, payment information, and personal details. It also helps improve trust and search engine ranking for websites.

    ![HttpVsHttps](/assets/httpVsHttps.webp)

10. #### **[HTTP/0.9](/null)**  
    HTTP/0.9, also known as "HTTP Version 0.9," was the first version of the Hypertext Transfer Protocol. It was a very basic and simple protocol, introduced in the early days of the World Wide Web. Here's a concise overview of HTTP/0.9:

    ![HTTP/0.9](/assets/http09.jpg)

    1. **Request-Only Protocol**: HTTP/0.9 was a request-only protocol, which means it only supported sending HTTP requests from the client to the server. It did not have a formalized way of handling HTTP responses.

    2. **No Headers**: HTTP/0.9 had no support for headers or metadata. A client would send a simple request, and the server would respond with the content of the requested resource without any additional information.

    3. **GET Method Only**: The only HTTP method supported in HTTP/0.9 was the GET method, which was used to request a resource from the server.

    4. **Text-Based**: Requests and responses were text-based, with the client sending a single line request like "GET /path/to/resource," and the server responding with the raw HTML content of the requested resource.

    5. **No Status Codes**: HTTP/0.9 did not include status codes or error handling mechanisms. If the requested resource was not found, the server would simply not respond.

    6. **Obsolete**: HTTP/0.9 is considered obsolete and was quickly replaced by more structured and robust versions of HTTP, such as HTTP/1.0 and subsequent versions.

11. #### **[HTTP/1.1](/null)**
    ![Http Timeline](/assets/HttpTimeline.jpg)

    HTTP/1.1, the second major version of the Hypertext Transfer Protocol, introduced several important enhancements and improvements over its predecessor, HTTP/1.0. A concise overview of HTTP/1.1:

    ![Http 1.1 Connection](/assets/http1.1Connection.jpeg)

    1. **Persistent Connections**: One of the significant improvements in HTTP/1.1 was the introduction of persistent connections. In HTTP/1.0, each request and response opened a new connection, but in HTTP/1.1, connections could be reused for multiple requests, reducing the latency and overhead. Using Header:
        ```HTTP
        Connection: keep-alive
        ```
    ![Persistant Connections](/assets/persistantConnection.png)

    2. **Host Header**: HTTP/1.1 introduced the `Host` header, which is mandatory in every request. It allows a single web server to host multiple websites, as the server uses the `Host` header to determine which site the client is trying to access.

    3. **Request Pipelining**: HTTP/1.1 supports request pipelining, which allows the client to send multiple requests before receiving responses. This reduces the latency by eliminating the need to wait for each response before sending the next request.  
    ![Pipelining](/assets/pipelining.svg)

    4. **Chunked Transfer Encoding**: HTTP/1.1 introduced the chunked transfer encoding mechanism, which enables the server to send data in chunks, making it possible to stream content and handle large files more efficiently.

    5. **Compression**: It added support for content compression, allowing the server to compress response data before sending it to the client. Common compression methods include gzip and deflate.

    6. **Caching Improvements**: HTTP/1.1 improved caching mechanisms, making it possible to cache responses more effectively, reducing the need to re-fetch identical content.

    7. **Range Requests**: Clients could now request specific ranges of a resource using the `Range` header, which is useful for resuming downloads and partial content retrieval.
        ```HTTP
        Range: <unit>=<range-start>-
        Range: <unit>=<range-start>-<range-end>
        Range: <unit>=<range-start>-<range-end>, <range-start>-<range-end>
        Range: <unit>=<range-start>-<range-end>, <range-start>-<range-end>, <range-start>-<range-end>
        Range: <unit>=-<suffix-length>

        ```

    8. **Status Codes**: HTTP/1.1 extended the range of status codes, introducing more specific codes to better indicate the outcome of a request, such as 201 Created and 206 Partial Content.

        1. Informational responses (100 – 199)
        2. Successful responses (200 – 299)
        3. Redirection messages (300 – 399)
        4. Client error responses (400 – 499)
        5. Server error responses (500 – 599)

    9. **Security**: Although not a security protocol in itself, HTTP/1.1 laid the groundwork for secure connections by integrating well with the HTTPS protocol.


12. #### **[HTTP/2](/null)**  

    ![Http 2.0 Connection](/assets/http2.0Connection.jpeg)
    HTTP/2, the second major version of the Hypertext Transfer Protocol, was introduced to address many of the performance limitations of HTTP/1.1. It brought several improvements for faster and more efficient web communication. A concise overview of HTTP/2:

    1. **Multiplexing**: One of the most significant changes in HTTP/2 is multiplexing, which allows multiple requests and responses to be sent and received concurrently on a single connection. This eliminates the need for multiple parallel connections, reducing latency and improving efficiency.  
    ![Request Multiplexing](/assets/requestMultiplexing.webp)

    2. **Header Compression**: HTTP/2 uses header compression to reduce overhead. Header fields are encoded and transmitted in a compressed binary format, which helps decrease the amount of data sent with each request and response.  
    ![Header Compression](/assets/headerCompression.webp)

    3. **Binary Protocol**: HTTP/2 uses a binary protocol instead of plain text, making it more efficient to parse and transmit, especially for machines.  
    ![Binary Protocol](/assets/binaryProtocol.webp)

    4. **Server Push**: HTTP/2 introduced server push, allowing the server to push additional resources to the client before the client requests them. This can improve page loading times by reducing the need for additional round-trip requests.
    ![Server Push](/assets/serverPush.webp)

    5. **Prioritization**: It supports stream prioritization, enabling clients to specify the importance of each request, allowing critical resources to be delivered faster.

    6. **Flow Control**: HTTP/2 has built-in flow control mechanisms, ensuring that overwhelmed clients can slow down the transmission of data to avoid congestion.

    7. **Improved Security**: While not a security protocol in itself, HTTP/2 is often used in conjunction with HTTPS to enhance security and privacy.

    8. **Backward Compatible**: HTTP/2 is designed to be backward compatible with HTTP/1.1, allowing older clients and servers to continue functioning without issues.

    9. **Reduced Latency**: By improving the efficiency of data transfer, HTTP/2 reduces page load times and latency, resulting in a better user experience.  
    ![Server Push latency](/assets/serverPushLatency.webp)

13. #### **[HTTP/3](/null)**  

    ![Quic](/assets/httpOverQuic.png)
    HTTP/3 is the third major version of the Hypertext Transfer Protocol, designed to further enhance web performance and security. It builds upon the foundation of HTTP/2 and introduces several notable changes. Here's a concise overview of HTTP/3:  

    ![HTTP comparisons](/assets/httpComparisons.webp)

    1. **QUIC Protocol**: HTTP/3 is built on top of the QUIC (Quick UDP Internet Connections) transport protocol, which offers improved connection management and reduced latency compared to TCP.  
    ![TCP vs Quic](/assets/TcpTlsVsQuic.gif)

    6. **Connection Migration**: HTTP/3 supports connection migration, allowing a client to switch between networks or IP addresses without breaking connections.

    7. **Error Handling**: It includes improved error handling mechanisms to detect and recover from issues more efficiently.

    8. **Backward Compatibility**: HTTP/3 is designed to be backward compatible with HTTP/2 and HTTP/1.1, ensuring that older clients and servers can still communicate.

    9. **Simplified Protocol**: HTTP/3 aims to simplify the protocol by reducing the complexities of HTTP/2, making it more robust and efficient.  

    ![HTTP Meme](/assets/tcpMeme.webp)

14. #### **[Caching](/null)**  
    Caching is a critical mechanism used in web applications to improve performance and reduce the load on servers. It involves storing and reusing previously fetched or computed data to minimize the need for redundant requests or computations. Here's a concise overview of caching:

    1. **Types of Caching**:  
        
        ![Cache Tiers](/assets/cacheTiers.jpeg)

        - **Browser Cache**: Web browsers store resources like images, stylesheets, and scripts locally to reduce the need for re-downloading them when revisiting a webpage.
        - **Content Delivery Network (CDN) Cache**: CDNs cache content closer to users, speeding up content delivery by serving cached data from nearby servers.
        - **Server-Side Cache**: Web servers and application servers can cache responses to reduce processing time for frequently requested data.
        - **Database Cache**: Database systems can cache query results to reduce the time required to fetch data from the database.  

        ![Cache At CDN](/assets/cacheAtCdn.png)

    2. **Cache Invalidation**: Caches need mechanisms to ensure that data remains up-to-date. Cache invalidation strategies include time-based expiration, versioning, and purging old or stale data.
        ```HTTP
        Cache-Control: no-store, no-cache, max-age=0, must-revalidate, proxy-revalidate
        Cache-Control: no-store
        Expires: Tue, 28 Feb 2022 22:22:22 GMT
        ```

    3. **Cache-Control Headers**: The `Cache-Control` header in HTTP responses is used to provide instructions to clients and intermediaries on how to cache and serve content. It includes directives like `max-age` for specifying cache duration and `no-cache` for revalidation.
        ```HTTP
        HTTP/1.1 200 OK
        Content-Type: text/html
        Content-Length: 1024
        Date: Tue, 22 Feb 2022 22:22:22 GMT
        Last-Modified: Tue, 22 Feb 2022 22:00:00 GMT
        Cache-Control: max-age=3600

        <!doctype html>
        …
        ```
        ```HTTP
        GET /index.html HTTP/1.1
        Host: example.com
        Accept: text/html
        If-Modified-Since: Tue, 22 Feb 2022 22:00:00 GMT

        ```


    4. **Etag and Last-Modified**: HTTP headers like `ETag` and options like `must-revalidate` are used for forcibly revalidating and re-fetching.
        ```HTTP
        Cache-Control: max-age=0, must-revalidate
        ```

    4. **Etag and Last-Modified**: HTTP headers like `ETag` and `Last-Modified` are used for conditional requests, enabling clients to validate cached content with the server before re-fetching.
        ```HTTP
        HTTP/1.1 304 Not Modified
        Content-Type: text/html
        Date: Tue, 22 Feb 2022 23:22:22 GMT
        Last-Modified: Tue, 22 Feb 2022 22:00:00 GMT
        ETag: "33a64df5"
        Cache-Control: max-age=3600
        ```
        ```HTTP
        GET /index.html HTTP/1.1
        Host: example.com
        Accept: text/html
        If-None-Match: "33a64df5"
        ```

    5. **Benefits**: Caching significantly improves website performance by reducing latency, bandwidth usage, and server load. It enhances user experience and responsiveness.

    6. **Challenges**: Proper cache management is essential, as improperly configured caches can serve outdated or incorrect content. Cache consistency and cache purging strategies need careful consideration.  
    ![Cache Hit ratio](/assets/cacheHit.webp)

15. #### **[Compression](/null)**
    ![Compression in HTTP](/assets/httpCompression.png)
    Compression in HTTP involves reducing the size of data transferred between clients and servers to improve the efficiency of web communication. It helps reduce bandwidth usage and load times. Here's a concise overview of compression in HTTP:

    1. **Gzip and Deflate**: Two common compression methods used in HTTP are Gzip and Deflate. These methods reduce the size of text-based resources, such as HTML, CSS, and JavaScript files, before they are transmitted.  
        ```HTTP
        GET /index.html? HTTP/1.1
        Accept: text/html
        Accept-Encoding: gzip;(qvalue), deflate;(qvalue)
        ```

    2. **Accept-Encoding Header**: Clients can specify their support for compression methods by sending an `Accept-Encoding` header in their requests. Servers use this information to determine whether to apply compression and which method to use.
        ```HTTP
        GET /index.html? HTTP/1.1
        Accept: text/html
        Accept-Encoding: gzip;(qvalue), deflate;(qvalue)
        ```

    3. **Content-Encoding Header**: When a server compresses a response, it includes a `Content-Encoding` header in the response to indicate which compression method was applied (e.g., "gzip" or "deflate").
        ```HTTP
        Content-Encoding: gzip
        Content-Encoding: compress
        Content-Encoding: deflate
        Content-Encoding: br

        // Multiple, in the order in which they were applied
        Content-Encoding: deflate, gzip
        ```

    4. **End To End Compression**: For compression, end-to-end compression is where the largest performance improvements of websites reside. End-to-end compression refers to a compression of the body of a message that is done by the server and will last unchanged until it reaches the client. Whatever the intermediate nodes are, they leave the body untouched.  
    ![End to End Compression](/assets/endToEndCompression.png)

    4. **Hop To Hop Compression**: Hop-by-hop compression, though similar to end-to-end compression, differs by one fundamental element: the compression doesn't happen on the resource in the server, creating a specific representation that is then transmitted, but on the body of the message between any two nodes on the path between the client and the server. Connections between successive intermediate nodes may apply a different compression.  
    ![Hop to Hop Compression](/assets/hopToHopCompression.png)
    ![Hop to Hop Compression](/assets/hopToHopCompressionDetailed.png)

    4. **Benefits**: Compression reduces the amount of data that needs to be transmitted over the network, resulting in faster page load times, lower bandwidth costs, and reduced server load.

    5. **Text Compression**: Compression is particularly effective for text-based resources because these resources typically contain repeated patterns that can be compressed.

    6. **Binary Resources**: Compression is less effective for binary resources, such as images and videos, as these formats are already compressed. Further compression may not yield significant reductions.

    7. **Combining with Caching**: Compression is often combined with caching to optimize web performance. Cached, compressed resources reduce load times and server requests.

16. #### **[Content Negotiation](/null)**  
    Content negotiation in HTTP is a mechanism that allows the client and server to agree on the most suitable representation of a resource, such as HTML or JSON, based on factors like the client's preferences, capabilities, and the server's available options. It helps ensure that the best content format is delivered for a particular request, improving user experience and compatibility across various devices. Content negotiation involves the following key points:
    ```HTTP
    GET /resource HTTP/1.1
    Host: example.com
    Accept: text/html, application/json
    Accept-Language: en-US, fr-FR
    Accept-Encoding: gzip, deflate
    Accept-Charset: utf-8, iso-8859-1
    ```

    1. **Client Preferences**: Clients can express their content format preferences using the `Accept` header in the HTTP request. For example, a client can indicate that it prefers JSON over XML.

    2. **Server Options**: The server provides multiple representations of a resource in different formats, such as HTML, JSON, or XML. These options are based on what the server can offer.

    3. **Content Negotiation Process**: The negotiation process occurs when the server receives a request. It considers the client's preferences and the available representations, then selects the most appropriate representation to send back in the response.  
    ![Content Negotiation Server](/assets/httpNegotiationServer.png)

    4. **Content-Type Header**: The server specifies the chosen representation's content type in the `Content-Type` header of the response, indicating the format of the content being sent.  
        ```http
        HTTP/1.1 200 OK
        Content-Type: application/json
        Content-Length: 123
        Date: Sun, 30 Oct 2023 12:00:00 GMT

        {
        "message": "This is a JSON response."
        }
        ```


17. #### **[Range Requests](/null)**
    Range requests in HTTP allow clients to request a specific range of data from a resource, such as a portion of a file or a segment of a large video. This mechanism is useful for resuming interrupted downloads, streaming media, and efficient data retrieval. A concise overview of range requests:

    1. **HTTP Range Header**: Range requests are made by including the `Range` header in the HTTP request. The header specifies the byte range or other units (e.g., time) the client wants to retrieve.  
        ```HTTP
        GET /large-file.zip HTTP/1.1
        Host: example.com
        Range: bytes=100-199
        ```

    2. **Partial Content**: If the server supports range requests, it responds with a `206 Partial Content` status code. The response includes the requested portion of the resource, along with the `Content-Range` header indicating the range provided.
        ```HTTP
        HTTP/1.1 206 Partial Content
        Content-Range: bytes 100-199/1000
        Content-Length: 100

        [Partial content here...]
        ```

    3. **Byte Ranges**: Byte ranges are the most common form of range requests. For example, a client can request bytes 100-199 of a file. This is useful for resuming downloads or fetching portions of a large file.
        ```HTTP
        GET /large-file.zip HTTP/1.1
        Host: example.com
        Range: bytes=100-199    
        ```

    4. **Other Units**: Range requests can also specify other units, such as time ranges for streaming media, making it versatile for various types of resources.
        ```HTTP
        GET /video-stream.mp4 HTTP/1.1
        Host: example.com
        Range: seconds=30-60
        ```

    5. **Content-Length**: The server may include the `Content-Length` header to indicate the total size of the resource. Clients can use this information to calculate the percentage of the content received.
        ```HTTP
        HTTP/1.1 200 OK
        Content-Length: 1000
        ```

    6. **Accept-Ranges Header**: The `Accept-Ranges` header in the response informs the client whether the server supports range requests. Common values are "bytes" for byte ranges and "none" if not supported.
        ```HTTP
        HTTP/1.1 200 OK
        Accept-Ranges: bytes
        ```

    7. **Conditional Requests**: Clients can use the `If-Range` header to ensure they receive the correct range by matching the resource's ETag or modification time. This helps prevent issues when a resource changes while the client requests it.
        ```HTTP
        GET /resource HTTP/1.1
        Host: example.com
        Range: bytes=100-199
        If-Range: "etag123"
        ```

18. #### **[Keep-Alive](/null)**
    "Keep-Alive" in HTTP, also known as "HTTP Keep-Alive" or "persistent connection," is a mechanism that allows multiple HTTP requests and responses to be sent over a single TCP connection. This eliminates the need to establish a new connection for each request, reducing latency and improving web performance. Key points about Keep-Alive include:

    ```HTTP
    GET /resource HTTP/1.1
    Host: example.com
    Connection: keep-alive
    ```

    ![KeepAlive](/assets/keepAlive.webp)

    - **Persistent Connection**: It keeps the connection open after the initial request/response, allowing multiple requests and responses to be exchanged over the same connection.
    - **Reduced Latency**: By avoiding connection establishment for each request, Keep-Alive reduces the time required to load web pages.
    - **Resource Efficiency**: Helps servers and clients use network and server resources more efficiently by reusing existing connections.
    - **Connection Header**: The `Connection: keep-alive` header is used to request or acknowledge the use of Keep-Alive in HTTP.
    - **Default in HTTP/1.1**: Keep-Alive is the default behavior in HTTP/1.1, whereas in earlier versions like HTTP/1.0, it needed to be explicitly requested.

19. #### **[Redirects](/null)**  

    ![Redirect](/assets/redirect.svg)
    Redirects in HTTP are mechanisms used to instruct web clients (such as browsers) to go to a different URL than the one initially requested. They serve various purposes, including handling moved content, ensuring security, and improving user experience. Key points about redirects include:

    ```HTTP
    HTTP/1.1 302 Found
    Location: https://example.com/new-location
    ```

    - **HTTP Status Codes**: Redirects are indicated by specific HTTP status codes, such as 301 (Moved Permanently), 302 (Found), and 307 (Temporary Redirect).
    - **URL Change**: Redirects can point to a new URL where the client should continue its request.
    - **Common Use Cases**: Redirects are used for moving content to a new location, handling user authentication, enforcing HTTPS, and managing URL canonicalization.
    - **Client Compliance**: Web clients, like browsers, automatically follow redirects based on the provided status codes.
    - **SEO Impact**: Redirects can impact search engine optimization (SEO), and the type of redirect used matters; for example, a 301 redirect is typically better for SEO than a 302 redirect.
    - **Cascading Redirects**: Multiple redirects can be chained together, with each redirect leading to another URL.

20. #### **[Referrer](/null)**  
    The "Referer" (spelled as "Referrer" in HTTP headers) is an HTTP header field that provides information about the source or referring webpage that linked to the current webpage. Key points about the "Referer" header include:  

    ```HTTP
    GET /page HTTP/1.1
    Host: example.com
    Referer: https://referrer-site.com/previous-page
    ```

    - **Usage**: It's used to track the origin of a request, helping websites understand where incoming traffic is coming from.
    - **Security Concerns**: The "Referer" header can raise security and privacy concerns, as it reveals information about a user's browsing habits.
    - **Spoofing**: The header can be spoofed or disabled in some cases to protect user privacy.
    - **Typo in Header Name**: The misspelling of "Referer" as "Referrer" is historical and has been retained for compatibility reasons.
    - **HTTP Header Field**: The "Referer" or "Referrer" information is transmitted as an HTTP header when a user clicks a link.

21. #### **[User Authentication](/null)**  
    User authentication in HTTP is the process of verifying the identity of a user or client before granting access to certain resources or services on a web server. It is essential for securing sensitive data and controlling access to protected areas. Key points about user authentication in HTTP include:

    - **Credentials**: Users provide their credentials, such as a username and password, to prove their identity.
        > `X-OpenID-Key=sdofhksudjbfkd,sjdbh`

    - **HTTP Authentication Methods**: Common authentication methods in HTTP include Basic Authentication, Digest Authentication, and Bearer Token Authentication.
        

        1. **Basic Authentication**:
            Basic Authentication sends the username and password in an encoded form over the network. It's not considered secure without additional encryption like HTTPS.

        2. **Digest Authentication**:
            Digest Authentication uses a challenge-response mechanism to verify the client's identity without transmitting the password itself. It offers better security than Basic Authentication.

        3. **Bearer Token Authentication**:
            Bearer Token Authentication involves sending a token (usually a JSON Web Token, JWT) with each HTTP request. The server validates the token to authenticate the client.

        4. **OAuth (Open Authorization)**:
            OAuth is an authorization framework that allows third-party applications to access a user's resources without sharing their credentials. It's commonly used for authentication with APIs and social media platforms.

        5. **OAuth 2.0**:
            OAuth 2.0 is the second version of OAuth and is widely used for authorization. It provides a way for applications to access resources on behalf of a user.

        6. **OpenID Connect**:
            OpenID Connect is built on top of OAuth 2.0 and provides identity information about the authenticated user. It is commonly used for single sign-on (SSO) and identity verification.

        7. **Token-Based Authentication**:
            Token-Based Authentication involves exchanging a username and password for a token. This token is used for subsequent requests, eliminating the need to send credentials with each request.

        8. **API Key Authentication**:
            API Key Authentication involves sending a unique API key with each request. The server validates the key to determine whether the client has access.

        9. **Client Certificate Authentication**:
            Client Certificate Authentication requires the client to present a digital certificate to the server. The server validates the certificate to authenticate the client.

        10. **Kerberos Authentication**:
            Kerberos is a network authentication protocol that uses symmetric key cryptography to authenticate clients and servers.

        11. **SAML (Security Assertion Markup Language)**:
            SAML is an XML-based standard for exchanging authentication and authorization data between parties, typically in single sign-on scenarios.

    - **Authorization Header**: Authentication credentials are typically included in the "Authorization" header of an HTTP request.  
        ```HTTP
        GET /api/resource HTTP/1.1
        Host: example.com
        Authorization: Bearer YOUR_ACCESS_TOKEN
        ```
    - **Session Management**: After successful authentication, a session is often established to maintain the user's authenticated state during subsequent requests.
    - **Cookies**: Cookies are frequently used to manage and track user sessions and authentication tokens.
        ```HTTP
        GET /example-page HTTP/1.1
        Host: example.com
        Cookie: session_id=ABC123; user_pref=dark-mode
        ```
    - **Security Measures**: To enhance security, it's important to use secure connections (HTTPS) to encrypt credentials and consider additional security measures like two-factor authentication (2FA).
