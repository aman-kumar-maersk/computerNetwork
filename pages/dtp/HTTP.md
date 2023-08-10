### [Home](/README.md)

# HyperText Transfer Protocol

HTTP is the protocol mainly used for transferring Web Pages and related resources over the Internet. It operates on top of [TCP](/pages/dtp/README.md#1-transmission-control-protocol-tcp) and follows a `Request - Response method.`

#### Following are some of the features of [HTTP Protocol](/null)

1. **[Stateless Protocol](/null)**  
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
        > `Authorisation: Bearer <JWT Token>`  

        ![JWT Authroisation](/assets/jwt.png)

    By utilizing cookies and session management, websites and applications can maintain state and offer personalized experiences to users while working within the stateless nature of the HTTP protocol.

2. [Request Methods (GET, POST, PUT, DELETE, etc.)](/null)  
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
4. [Headers](/null)
5. [Request Body](/null)
6. [Response Body](/null)
7. [URL (Uniform Resource Locator)](/null)
8. [Cookies](/null)
9. [HTTPS (Hypertext Transfer Protocol Secure)](/null)
10. [HTTP/0.9](/null)
11. [HTTP/1.1](/null)
12. [HTTP/2](/null)
13. [HTTP/3](/null)
14. [Caching](/null)
15. [Compression](/null)
16. [Content Negotiation](/null)
17. [Range Requests](/null)
18. [Keep-Alive](/null)
19. [Redirects](/null)
20. [Referrer](/null)
21. [User Authentication](/null)
22. [Content-Type Negotiation](/null)