# API Reference

Base URL: `http://localhost:8000`

## Endpoints

### Health

`GET /health` — Returns service status and dependency health.

```bash
curl http://localhost:8000/health
```

### Authentication

#### Register an account

`POST /auth/register` — Create a new account and obtain a JWT access token.

```bash
curl -X POST http://localhost:8000/auth/register \
  -H "Content-Type: application/json" \
  -d '{
    "email": "user@example.com",
    "password": "password123"
  }'
```

#### Log in

`POST /auth/login` — Log in and obtain a JWT access token.

The login endpoint accepts form data. Use the account email as the `username` value.

```bash
curl -X POST http://localhost:8000/auth/login \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "username=user@example.com&password=password123"
```

The authentication response contains an access token:

```json
{
  "access_token": "<access-token>",
  "token_type": "bearer"
}
```

Use this token in the `Authorization` header for protected endpoints:

```bash
-H "Authorization: Bearer <access-token>"
```

### Profiles

All profile endpoints require authentication.

#### Create a profile

`POST /profiles` — Create a profile with an optional GitHub username, portfolio URL, and resume file.

```bash
curl -X POST http://localhost:8000/profiles \
  -H "Authorization: Bearer <access-token>" \
  -F "github_username=example-user" \
  -F "portfolio_url=https://example.com" \
  -F "resume_file=@/path/to/resume.pdf"
```

The resume must be a PDF, Markdown, or plain-text file. Each profile field is optional, so fields that are not needed may be removed from the command.

#### Retrieve a profile

`GET /profiles/{profile_id}` — Retrieve a profile owned by the authenticated user.

```bash
curl http://localhost:8000/profiles/<profile-id> \
  -H "Authorization: Bearer <access-token>"
```

Replace `<profile-id>` with the UUID of the profile.

#### Delete a profile

`DELETE /profiles/{profile_id}` — Delete a profile and its associated data.

```bash
curl -X DELETE http://localhost:8000/profiles/<profile-id> \
  -H "Authorization: Bearer <access-token>"
```

Replace `<profile-id>` with the UUID of the profile.

### Reviews

All review endpoints require authentication.

#### Request a review

`POST /reviews` — Request a new portfolio review for a profile.

```bash
curl -X POST http://localhost:8000/reviews \
  -H "Authorization: Bearer <access-token>" \
  -H "Content-Type: application/json" \
  -d '{
    "profile_id": "<profile-id>"
  }'
```

Replace `<profile-id>` with the UUID of a profile owned by the authenticated user.

#### Retrieve a review

`GET /reviews/{review_id}` — Retrieve a review owned by the authenticated user.

```bash
curl http://localhost:8000/reviews/<review-id> \
  -H "Authorization: Bearer <access-token>"
```

Replace `<review-id>` with the UUID of the review.

#### List reviews

`GET /reviews` — List reviews for the authenticated user.

```bash
curl "http://localhost:8000/reviews?page=1&page_size=20" \
  -H "Authorization: Bearer <access-token>"
```

The `page` parameter must be at least `1`. The `page_size` parameter can contain a value from `1` through `100` and defaults to `20`.

## Interactive Docs

When the API is running, visit:

- **Swagger UI:** http://localhost:8000/docs
- **ReDoc:** http://localhost:8000/redoc
