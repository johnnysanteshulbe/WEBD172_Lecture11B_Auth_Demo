# WEBD 172 — Lecture 11C JWT Authentication Demo

This project extends the Lecture 11B registration/login demo and adds:

- JSON Web Tokens (JWT)
- `jsonwebtoken`
- `.env` configuration with `dotenv`
- Bearer tokens
- authentication middleware
- `jwt.verify()`
- `req.user`
- a protected `/api/profile` route

## Install

```bash
npm install
```

## Environment File

Copy `.env.example` and rename the copy to `.env`.

You can generate a secret by doing the following:

node -e "console.log(require('crypto').randomBytes(32).toString('hex'))"

Then add your secret:

```text
JWT_SECRET=your_long_random_secret_here
```

Do not commit `.env` to GitHub.

## Start MongoDB

This demo uses:

```text
mongodb://127.0.0.1:27017/authDemo
```

## Start the Server

```bash
npm start
```

or:

```bash
npm run dev
```

Server:

```text
http://localhost:3000
```

## Register

POST:

```text
http://localhost:3000/api/register
```

JSON body:

```json
{
  "name": "Test Student",
  "email": "student@example.com",
  "password": "mesa123"
}
```

## Login

POST:

```text
http://localhost:3000/api/login
```

JSON body:

```json
{
  "email": "student@example.com",
  "password": "mesa123"
}
```

A successful login now returns a token:

```json
{
  "message": "Login successful",
  "token": "..."
}
```

Copy the token.

## Protected Profile Route

GET:

```text
http://localhost:3000/api/profile
```

First test it without a token. You should receive:

```text
401 Unauthorized
```

Then add this request header:

```text
Authorization: Bearer YOUR_TOKEN_HERE
```

A valid token should return the user's profile without the password field.
