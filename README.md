# భగవద్గీత — Clean Source Project

This is a React + TypeScript + Vite starter app configured for the GitHub repository `bagavathgeetha`.

## Features
- Telugu UI and all 18 chapter names
- Chapter selector and shloka list (Chapter 1 appears first)
- Clicking a shloka attempts to play its matching local MP4
- Responsive desktop/mobile layout
- GitHub Actions workflow builds and deploys the app to GitHub Pages

## Important
This clean project intentionally has no Google Drive URLs, video IDs, or private videos. Add your own media to `public/videos/` and update `src/data.ts` with the correct file counts and paths. Currently Chapter 1 has 47 placeholder entries; other chapters start with one placeholder entry each.

## GitHub
Upload all files and folders from this project to the repository's `main` branch. The included workflow under `.github/workflows/deploy.yml` builds and deploys automatically after a push. Check the repository's Actions tab for the build/deploy result.

The Vite base path is set to `/bagavathgeetha/` for the repository URL shown in the user's screenshots.