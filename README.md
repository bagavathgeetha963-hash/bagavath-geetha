# Bhagavad Gita — Private Video Project

This starter keeps private video URLs and media IDs out of the public frontend repository. The browser requests a video by chapter/shloka number from a backend endpoint. The backend resolves the actual media location from server-side environment variables and streams it to authorized users.

## Important security facts
- Never put private Drive URLs, access tokens, video IDs, or secrets in frontend code or a public GitHub repository.
- GitHub Pages is static hosting and cannot securely store secrets or run this backend. Host the `server/` API on a backend host that supports environment variables and private media access.
- This project includes a secure-by-default video resolver interface, but it does not connect to Google Drive by itself. Configure a trusted private media provider in the backend.
- A sign-in / authorization policy must be configured before real private videos are served. The included demo API denies playback until `VIDEO_ACCESS_TOKEN` is configured and the request includes that token. For production, replace the simple bearer token with proper user authentication.
- This ZIP contains no actual videos, Google Drive links, or provider IDs.

## Run
### Frontend
`cd client`
`npm install`
`npm run dev`

### Backend
`cd server`
`npm install`
`npm run dev`

Set `VIDEO_ACCESS_TOKEN` in the backend environment before testing authorized playback. Do not commit `.env`. Copy `.env.example` to `.env` only for local development.

## Add private media provider
Edit `server/src/mediaProvider.ts`. Implement `getPrivateMediaStream(chapter, shloka)` using a private storage provider API and server-side secrets. It must return a readable stream and a valid content type. Do not return the underlying provider URL or ID to the frontend.
