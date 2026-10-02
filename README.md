# BlogAPI

BlogAPI is my first personal project: a REST API for a blogging platform, built independently with Java 17 and Spring Boot. I designed the PostgreSQL schema and implemented the backend myself; no AI-generated code was used for the backend. This project was my first end-to-end experience with API design, authentication, persistence, and deployment.

## Project links

- **[Live frontend demo](https://blogapi-demo-frontend.onrender.com)** — an AI-generated demo client for exploring the API. The backend is my work; the frontend is included to demonstrate how a client can use it.
- **[Swagger API documentation](https://adam-elzahiri.github.io/blog-api/)** — browse endpoints, parameters, and request bodies in Swagger UI.
- **[OpenAPI specification](docs/api-docs.json)** — import the API contract into tools such as Postman or Insomnia.

## What the API does

- **Authentication and profiles:** username/password registration and login, JWT-protected routes, public user profiles, and profile picture upload, replacement, and deletion.
- **Blog posts:** create, read, update, and delete posts; browse paginated results and filter by author.
- **Comments:** CRUD operations, nested replies, and paginated comment lists.
- **Reactions:** like or dislike posts, change or remove a reaction, and browse reactions by type.
- **File storage:** profile pictures are uploaded to Cloudinary. The API stores the Cloudinary public ID with the user record and returns an image URL in profile data.
- **API contract:** OpenAPI documentation describes the available endpoints and request formats.

## Engineering notes

- The PostgreSQL schema was designed for this project, with relationships between users, posts, comments, and reactions.
- Spring Security and JWTs protect authenticated operations; user-specific actions are handled by the backend.
- Reaction totals are calculated from reaction records when queried rather than maintained as stored counters. The trade-off is documented in [ADR 0001](adr/0001-reaction-count.md).
- The application is packaged with Docker and deployed on Render.

## Try the API

The backend is deployed on Render and may take a little time to respond to its first request.

- **Backend base URL:** `https://blogapi-0hdr.onrender.com`
- **API prefix:** `/api`

Append `/api` and the endpoint path shown in Swagger UI to the backend URL. For example, registration is:

```http
POST https://blogapi-0hdr.onrender.com/api/auth/register
```

For a protected endpoint, register or log in to obtain a JWT and send it as a bearer token:

```http
Authorization: Bearer YOUR_TOKEN_HERE
```

## Technology

Java 17 · Spring Boot · Spring Security · Spring Data JPA / Hibernate · PostgreSQL · Maven · Cloudinary · OpenAPI / Swagger · Docker

## License

Licensed under the [MIT License](LICENSE).
