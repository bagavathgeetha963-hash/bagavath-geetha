# Bhagavad Gita — Complete Private Video App

This project separates public source code from private video metadata.

## What is included
- Telugu React UI for all 18 chapters
- Shloka selector and video player
- Node.js/Express backend with access-token check
- Google Drive API streaming adapter using server-side service-account credentials
- GitHub Actions workflow to build the frontend
- No Drive IDs, Drive URLs, or private media inside this public source ZIP

## Important architecture
GitHub Pages is static hosting. It cannot run the backend or securely hold service-account keys. Deploy `client/` to static hosting and `server/` to a backend host that supports secrets. Put the private manifest and Google service-account credentials on the backend only.

## Setup
1. Upload this project's public files to GitHub.
2. Deploy `client/` as a static site. Set `VITE_API_BASE_URL` to your backend URL before building.
3. Deploy `server/` to a Node.js host.
4. In the backend host's private filesystem, place `video-manifest.json` at `server/private-data/video-manifest.json`. This file comes from the separate private manifest ZIP and must never be committed to public GitHub.
5. Add the Google service-account JSON as a host secret/file (`GOOGLE_APPLICATION_CREDENTIALS` path) and share the relevant Drive files/folders with that service-account email, with read access.
6. Set `VIDEO_ACCESS_TOKEN` as a long random secret in the backend host.
7. Configure frontend `VITE_VIDEO_ACCESS_TOKEN` only if this is a private single-user deployment. For multi-user use, implement real user login instead; a token compiled into a public frontend is not a secret.

## Honest limitations
The private manifest preserves the file IDs and labels from the supplied JSON lists. Some entries have no reliable shloka number or have unusual labels; those are kept as unassigned rather than guessed. The Chapter 1 list is taken from the available existing chapter-1 manifest. Google Drive API access and playback have not been tested in this environment.
