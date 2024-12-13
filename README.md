# API Gateway Design Approach

## Overview
This document provides an overview of the approach taken to design the API Gateway and outlines key decisions made during the development process. It also highlights future improvements and steps that could be taken with more time.

## Approach

### 1. **Proper HTTP Methods**
The API Gateway follows standard HTTP method conventions, ensuring that each endpoint corresponds to an appropriate method for resource management:
- **GET**: Retrieve resource data.
- **POST**: Create new resources.
- **PUT**: Update existing resources.
- **DELETE**: Remove resources.

### 2. **Resource-Based URI Naming**
The naming of API Gateway URIs/endpoints follows a resource-based pattern to ensure clarity and maintainability. Each URI represents a specific resource and its associated actions:
- **GET /users**: Retrieve the list of users.
- **POST /users**: Create a new user.
- **PUT /users/{id}**: Update the user with the given ID.
- **DELETE /users/{id}**: Delete the user with the given ID.

This resource-based structure is designed to be both RESTful and intuitive for the API consumers.

## Key Decisions
- **Standardized HTTP Methods**: Following RESTful practices, appropriate HTTP methods were used to represent actions on resources, aligning with industry standards for API design.
- **Clear Endpoint Structure**: The URIs were designed to be clear and descriptive, making the API easier to understand and use for developers.
- **Scalable Design**: The choice of using an API Gateway allows for scalability, enabling future expansion and integration of additional services.

## Future Improvements (Given More Time)
If more time were available, the following improvements and features would be implemented:

### 1. **API Versioning**
API versioning would be added to ensure backward compatibility as the API evolves over time. This would allow for smooth transitions when new versions of the API are released, without breaking existing client integrations. Versioning would be implemented using a version number in the URI path. For example:
- **v1** (initial version):
    - **GET /v1/users**: Retrieve the list of users.
    - **POST /v1/users**: Create a new user.
    - **PUT /v1/users/{id}**: Update the user with the given ID.
    - **DELETE /v1/users/{id}**: Delete the user with the given ID.

- **v2** (future version):
    - **GET /v2/users**: Retrieve the list of users (with possible new features).
    - **POST /v2/users**: Create a new user (with potential changes).
    - **PUT /v2/users/{id}**: Update the user with the given ID (with potential improvements).
    - **DELETE /v2/users/{id}**: Delete the user with the given ID (with potential changes).

Versioning would allow the flexibility to introduce breaking changes in the API without disrupting clients using older versions.

### 2. **Unit Testing and Integration Testing**
Unit testing and integration testing would be conducted to ensure the reliability and correctness of the API Gateway. Tools like JUnit would be used for creating and running the tests, covering scenarios such as:
- Valid and invalid HTTP methods.
- Correct URI mapping.
- Response formatting.

### 3. **Custom Filters for HTTP Method Transformation**
To increase the flexibility of the API Gateway, custom filters would be created to modify the HTTP methods used in the API Gateway endpoint and transform them before forwarding to the downstream services. For example:
- **PUT requests** would be transformed into **POST** requests for certain endpoints that require a different method for updating data.
- **DELETE requests** could be converted into **POST** requests for services that only accept POST, but the endpoint's functionality still reflects the removal of a resource.

This transformation would allow the API Gateway to interact with services that may not support all HTTP methods natively, ensuring seamless integration across various services.

## Conclusion
The design of the API Gateway follows RESTful principles with proper HTTP methods and a resource-based URI pattern. API versioning would be introduced in the future to support backward compatibility as the system evolves. Given more time, the focus would shift toward enhancing the system's reliability and flexibility through comprehensive testing and method transformation features.
