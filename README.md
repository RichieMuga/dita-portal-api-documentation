# DITA Portal API Documentation

## Motivation

The DITA Portal API is designed to streamline the technical writing workflow, making content creation, management, and interaction more efficient for writers and contributors. By providing a comprehensive set of endpoints, we aim to:

- Simplify article creation and management
- Enable seamless commenting and interaction
- Support intuitive like and engagement features
- Provide a robust backend for technical writing collaboration

## API Endpoints

### Authentication

All routes requiring authentication use an `authToken` in the request body.

### Articles

#### Create Article
- **Route:** `POST /api/technical-writing/articles`
- **Body:** 
  - `title`: Article title
  - `content`: Article content
  - `coverImage`: Image URL
  - `authToken`: Authentication token

#### Get All Articles
- **Route:** `GET /api/technical-writing/articles`

#### Get Single Article
- **Route:** `GET /api/technical-writing/articles/article`
- **Parameters:**
  - `articleId`: Specific article ID
  - Optional `authToken` for author-specific access

#### Update Article
- **Route:** `PATCH /api/technical-writing/articles/my-articles`
- **Parameters:**
  - `articleId`: Article to update
  - `authToken`: Authentication token
- **Body:** Updated article details

#### Delete Article
- **Route:** `DELETE /api/technical-writing/articles`

### Comments

#### Create Comment
- **Route:** `POST /api/technical-writing/articles/article/{articleId}/comments`
- **Body:**
  - `text`: Comment content
  - `authToken`: Authentication token

#### Get Comments
- **Route:** `GET /api/technical-writing/articles/article/{articleId}/comments`
- **Query Parameters:**
  - `page`: Page number
  - `limit`: Comments per page

#### Update Comment
- **Route:** `PATCH /api/technical-writing/articles/article/{articleId}/comments/comment/{commentId}`
- **Body:**
  - `text`: Updated comment text
  - `authToken`: Authentication token

#### Delete Comment
- **Route:** `DELETE /api/technical-writing/articles/article/{articleId}/comments/comment/{commentId}`
- **Body:**
  - `authToken`: Authentication token

### Likes

#### Like Article
- **Route:** `POST /api/technical-writing/articles/article/{articleId}/like`
- **Body:**
  - `authToken`: Authentication token

#### Unlike Article
- **Route:** `DELETE /api/technical-writing/articles/article/{articleId}/like`
- **Body:**
  - `authToken`: Authentication token

#### Like Comment
- **Route:** `POST /api/technical-writing/articles/article/{articleId}/comments/comment/{commentId}/like`
- **Body:**
  - `authToken`: Authentication token

#### Unlike Comment
- **Route:** `DELETE /api/technical-writing/articles/article/{articleId}/comments/comment/{commentId}/like`
- **Body:**
  - `authToken`: Authentication token

### Image Upload

#### Upload Article Image
- **Route:** `POST /api/technical-writing/images/upload`
- **Content-Type:** `multipart/form-data`

## Getting Started

1. Obtain an authentication token
2. Use the appropriate endpoints for your desired action
3. Include the `authToken` in the request body for authenticated routes

## Notes

- All routes are prefixed with `http://localhost:3000/api/technical-writing/`
- Authentication is required for most write operations
- Ensure you have a valid `authToken` for authenticated requests

## Future Improvements

- Add more comprehensive error handling
- Implement more advanced filtering and searching
- Enhance security measures
- Add rate limiting and pagination improvements
