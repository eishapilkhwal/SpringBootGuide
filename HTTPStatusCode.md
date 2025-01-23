# HTTP Status Codes

HTTP Status Codes are three-digit numeric codes returned by a web server as part of its response to an HTTP request made by a client (e.g., browser, API client, etc.). These codes convey essential information about the result or status of the requested operation.

HTTP status codes are grouped into **five categories** based on their first digit:

---

## **1xx Informational**
The **1xx status codes** indicate that the request was received and understood, and the server is continuing to process it. These are used for informational purposes and are rarely encountered in practical applications.

### Examples:
- **100 Continue**: The server has received the initial part of the request, and the client should continue with the rest of the request.
- **101 Switching Protocols**: The server is switching to a different protocol as requested by the client (e.g., upgrading to WebSocket).

---

## **2xx Successful**
The **2xx status codes** indicate that the client's request was successfully received, understood, and processed by the server.

### Examples:
- **200 OK**:  
  The request was successful, and the server is returning the requested resource (e.g., a web page or API response).

- **201 Created**:  
  The request has been fulfilled, and a new resource has been created as a result (commonly used for POST requests).

- **204 No Content**:  
  The request was successful, but the server is not returning any content in the response body (typically used for operations like successful deletions).

---

## **3xx Redirection**
The **3xx status codes** indicate that further action is needed to complete the request. These are used when the client needs to take additional steps, such as redirecting to another URL, to access the requested resource.

### Examples:
- **301 Moved Permanently**:  
  The requested resource has been permanently moved to a different URL. The client should update its references to the new URL.

- **302 Found**:  
  The requested resource has been temporarily moved to a different URL. The server typically includes a `Location` header specifying the temporary URL to redirect the client.

- **304 Not Modified**:  
  The requested resource has not been modified since the last access. The client can use its cached version of the resource, and no new data is sent.

---

## **4xx Client Errors**
The **4xx status codes** indicate that there was an error on the client's part, such as a malformed request or authentication issues.

### Examples:
- **400 Bad Request**:  
  The server cannot understand or process the request due to invalid syntax or other client-side errors.

- **401 Unauthorized**:  
  The client must provide valid authentication credentials to access the requested resource.

- **403 Forbidden**:  
  The client is authenticated but does not have permission to access the requested resource.

---

## **5xx Server Errors**
The **5xx status codes** indicate that there was an error on the server's part while trying to fulfill the request. These errors suggest that the problem lies with the server, not the client.

### Examples:
- **500 Internal Server Error**:  
  A generic error message indicating that something went wrong on the server. The exact issue is unspecified, but the server could not process the request.

- **502 Bad Gateway**:  
  The server, acting as a gateway or proxy, received an invalid response from an upstream server.

- **503 Service Unavailable**:  
  The server is temporarily unable to handle the request due to maintenance or being overloaded.

---

## Summary Table of HTTP Status Code Categories

| Status Code Range | Category         | Description                                                             |  
|--------------------|------------------|-------------------------------------------------------------------------|  
| **1xx**            | Informational    | The server has received the request and is processing it.               |  
| **2xx**            | Successful       | The request was successfully processed by the server.                   |  
| **3xx**            | Redirection      | Further action is required to access the requested resource.            |  
| **4xx**            | Client Error     | There was an error on the client’s part, such as invalid input.          |  
| **5xx**            | Server Error     | The server failed to fulfill a valid request due to internal issues.     |  

---

By understanding HTTP status codes, developers and users can diagnose and resolve issues effectively, making web applications more robust and user-friendly.  
