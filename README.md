# color_profile

A small Express profile page whose background colour can be changed from an `iro.js` colour picker.

## What it does

The page renders a static profile card and an `iro.js` colour picker. Picking a colour updates the page live; the Update Profile button posts the value to `POST /setColor`, and the server keeps it in memory for subsequent requests. Card text switches to the inverted colour for contrast.

## Stack

- Node.js with Express 4 and EJS
- `iro.js` colour picker, Bootstrap and jQuery from CDN
- Docker image based on `node:lts`

## Getting started

```bash
npm install
node server.js
# http://localhost:3000
```

Or with Docker:

```bash
docker build -t color_profile .
docker run --rm -p 3000:3000 color_profile
```

## Notes

- The colour is a single in-process value, shared by every visitor and reset when the server restarts. There is no database or account.
- `server.js` listens on port 3000.
- The Dockerfile also copies a `flag.txt` into the image; that file is not in the repository, so a local `docker build` needs it next to the Dockerfile.
