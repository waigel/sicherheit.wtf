---
description: Disable Content-Type sniffing to prevent XSS attacks
---

# Header X-Content-Type-Options: nosniff

The header `X-Content-Type-Options: nosniff` is being introduced to disable the MIME type sniffing process in modern browsers. 
By setting this header, the browser is instructed not to automatically analyze and interpret the received content but to respect the specified Content-Type.


## Why is the header important?

The `Content-Type` header is usually used to send the received content type to the client, allowing the client to process the content correctly. When the Content-Type header is missing, a modern browser attempts to identify the content based on magic bytes, a process known as MIME type sniffing. However, MIME type sniffing can lead to unpredictable behavior and security issues. There is a possibility that a browser may misinterpret the content and potentially execute malicious code when MIME type sniffing is applied.

## Procedure

1. Verify that the `Content-Type` header is correctly set in all responses. This is usually handled automatically by frameworks like Spring and other services.
2. To avoid MIME type sniffing, add the `X-Content-Type-Options: nosniff` header to every response. It is helpful to set this header e.g. on proxy or load balancer level.


## Sources

- https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types#important_mime_types_for_web_developers