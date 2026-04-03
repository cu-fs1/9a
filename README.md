# Next.js Static Export with Docker & Nginx

This project demonstrates a streamlined Next.js application configured for static export and strictly deployed using Docker with an Nginx server. 

## Features

- **Next.js Static Export**: Fully static build generated in the `/out` directory. No Node.js server required at runtime.
- **Nginx Serving**: Robust, lightweight production-grade web serving over port 8080.
- **pnpm Driven**: Dependencies and builds are strictly locked to `pnpm` for faster, reproducible performance.
- **Modern UI**: Tailored with a custom glassmorphism entry page using Tailwind CSS v4.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/) installed on your machine.
- Optional: `pnpm` installed locally if you want to run the project outside of Docker.

## How to Run

1. **Build and Start the Container**

The application environment is orchestrated entirely through Docker Compose. Run the following command to build the image and start the Server instance:

```bash
docker compose up -d --build
```

2. **View the Application**

Once the container reports as `Up`, open your browser and navigate to:

👉 **[http://localhost:8080](http://localhost:8080)**

## Configuration Details

- **next.config.ts**: Configured with `output: "export"` and `images: { unoptimized: true }` to satisfy static export requirements.
- **Dockerfile**: Uses a multi-stage approach taking a `node:slim` foundation to build your app using `pnpm` and an `nginxinc/nginx-unprivileged` rootless runner to host the output static files.
- **compose.yml**: Exposes the containerized Nginx instance on `8080` port mapping.

## Stopping the Server

To stop the running application, execute:

```bash
docker compose down
```
