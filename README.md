# P2.Dev API Style Specification

## Overview

This specification outlines the API style to be used across all applications, single-page applications (SPAs), and API backends developed and deployed under the P2.Dev ecosystem. The primary goal is to ensure consistency, security, and ease of use across various platforms.

## Content Type

- All API interactions must use `application/json` as the content type for both requests and responses.

## Authentication

- APIs can be either open or protected.
- Protected APIs require a valid JSON Web Token (JWT) provided in the header as follows: `Authorization: Bearer TOKEN`.

## HTTP Status Codes

API responses are limited to the following HTTP status codes to streamline client handling:

- `200` - Success: The request was successful, and the response body contains the requested data.
- `401` - Unauthorized: A valid JWT is required but was not provided or is invalid.
- `412` - Precondition Failed: Indicates the requesting user must complete some form of onboarding (e.g., setting their display name).
- `500` - Internal Server Error: A generic error message indicating a server-side problem.

## Base Models

To promote uniformity, the following base models are defined for use across compliant servers:

### StatusMsg

A generic object for returning a message within a JSON object.

```json
{
  "message": "string"
}
```

### ErrorMsg

A generic object for returning a message within a JSON object.

```json
{
  "code": "string",
  "message": "string"
}
```

### DisplayableEntity

A base object representing entities that can be displayed. It includes an ID, a display name, and an avatar URL.

```json
{ 
  "id": "xxxx-xxxx", 
  "displayName": "John Smith", 
  "avatarUrl": "example.com/avatar.jpg" 
}
```

## Optional Base APIs

The following set of optional base APIs can be included by servers to support common functionalities:

### Notifications

A simple endpoint for registering device tokens for push notifications.

- **Method:** PUT
- **Endpoint:** `/notifications/:platform/:deviceToken`
- **Parameters:**
    - `platform`: Specifies the platform, supporting "ios" or "android".
    - `deviceToken`: The device token provided by mobile devices for push notification services.

## Conclusion

This specification aims to standardize API interactions within the P2.Dev ecosystem, ensuring a consistent and efficient development experience across all platforms. Compliance with this specification is expected to facilitate integration, improve security, and enhance overall system reliability.
