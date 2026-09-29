# OWASP Juice Shop Architecture

## Architecture Overview

OWASP Juice Shop follows a client-server web application architecture.

The user interacts with the application through a web browser. The frontend is implemented as an Angular Single Page Application (SPA), which runs on the client side after being delivered by the backend.

The Angular frontend communicates with the Node.js/Express backend using HTTP requests to REST API endpoints, mainly under `/api` and `/rest`.

The Node.js/Express backend is responsible for application routing, authentication, JWT handling, business logic, and communication with the data layer.

Sequelize is used as the Object Relational Mapping (ORM) layer between the backend application and the SQLite database. It allows the backend to interact with application data through defined models and database queries.

The application uses SQLite as its main relational database. The database file is stored at:

`data/juiceshop.sqlite`

The application is containerised using Docker and is exposed through port `3000`.

## Main Components

### User Browser
The browser is the external client used to access the application.

### Angular SPA
The Angular Single Page Application provides the client-side user interface and sends requests to the backend REST API.

### Node.js / Express Backend
The backend provides the main server-side functionality of the application, including:

- REST API routes
- Authentication and JWT handling
- Business logic
- Application routing
- Communication with the data layer

### Sequelize ORM
Sequelize acts as the abstraction layer between the backend and the SQLite database.

### SQLite Database
SQLite stores the application data in the file:

`data/juiceshop.sqlite`

## Data Flow

The main application data flow is:

1. The user accesses the application through a web browser.
2. The Node.js/Express server delivers the Angular frontend to the browser.
3. The Angular SPA sends HTTP requests to REST endpoints such as `/api` and `/rest`.
4. The Node.js/Express backend processes the request and applies authentication or business logic where required.
5. The backend accesses application data through Sequelize.
6. Sequelize performs the required read or write operations on the SQLite database.
7. The result is returned through the backend to the Angular frontend and displayed to the user.

## Trust Boundaries

The architecture contains two main trust boundaries.

### Client-to-Application Trust Boundary
The first trust boundary exists between the external client environment and the backend application.

The browser and Angular SPA are considered client-controlled components. Requests crossing this boundary must be treated as untrusted input and validated by the backend.

### Application-to-Data Trust Boundary
The second trust boundary exists between the application logic and the persistence layer.

The backend communicates with the SQLite database through Sequelize. Data crossing this boundary should be handled securely to prevent risks such as injection, unauthorized data access, or manipulation.

## Deployment

The application is deployed using Docker.

The Docker container runs the Node.js/Express application and its supporting application components. Port `3000` is exposed so that the application can be accessed from the host system.

The current deployment is started using Docker Compose.