# wayoyo/node:latest

A lightweight Node.js container based on Ubuntu 24.04, designed for general Node.js development.

---

## Features

- Based on Ubuntu 24.04
- Node.js (from official node:bookworm image)
- Includes `pnpm` as a fast, disk space-efficient package manager
- Exposes port 3000 (typical for Node.js development)
- Minimal and ready for development

---

## Available Tags

Currently, only the `:latest` tag is available for this image:

- `wayoyo/node:latest`

You can use this tag directly, or pull it as `wayoyo/node:ubuntu-24.04-latest` if you prefer a more descriptive name.

### How to add more tags

If you want to create and use additional tags (for example, for different versions or variants), you can do so by building and pushing the image with a new tag:

```bash
# Build with a new tag
docker build -t wayoyo/node:v1 .

# Tag an existing image
docker tag wayoyo/node:latest wayoyo/node:ubuntu-24.04-latest

# Push the new tag to Docker Hub
docker push wayoyo/node:v1
docker push wayoyo/node:ubuntu-24.04-latest
```

---

## Usage

### Pull the image

```bash
docker pull wayoyo/node:latest
```

### Basic usage

#### Interactive shell
Run the container with an interactive bash shell:

```bash
docker run -it wayoyo/node:latest
```

#### Run Node.js interactively
```bash
docker run -it wayoyo/node:latest node
```

### Development workflow

#### Mount your project directory
For development, mount your local project directory to the container's `/app` directory:

```bash
docker run -it -v $(pwd):/app wayoyo/node:latest
```

#### Run a Node.js script
```bash
docker run -v $(pwd):/app wayoyo/node:latest node your_script.js
```

#### Development with port mapping
If your Node.js application serves on port 3000 (or any other port), map it to your host:

```bash
docker run -it -p 3000:3000 -v $(pwd):/app wayoyo/node:latest
```

### Common use cases

#### Web application development
For web applications that serve on port 3000:

```bash
# Navigate to your project directory
cd /path/to/your/node/project

# Run with port mapping and volume mount
docker run -it -p 3000:3000 -v $(pwd):/app wayoyo/node:latest

# Inside the container, install dependencies and run your app
npm install
npm start
```

#### Using pnpm
```bash
# Install dependencies with pnpm
docker run -it -v $(pwd):/app wayoyo/node:latest pnpm install
```

#### One-off script execution
```bash
# Run a single Node.js script and exit
docker run --rm -v $(pwd):/app wayoyo/node:latest node script.js
```

### Environment variables

You can pass environment variables to customize the container behavior:

```bash
docker run -it -e NODE_ENV=development -v $(pwd):/app wayoyo/node:latest
```

### Docker Compose usage

Create a `docker-compose.yml` file for easier development:

```yaml
version: '3.8'
services:
  node-dev:
    image: wayoyo/node:latest
    ports:
      - "3000:3000"
    volumes:
      - .:/app
    environment:
      - NODE_ENV=development
    working_dir: /app
    tty: true
    stdin_open: true
```

Then run:
```bash
docker-compose up -d
docker-compose exec node-dev bash
```

---

## Build locally

If you want to build the image locally:

```bash
git clone <repository-url>
cd Dockerfile/docker/node/ubuntu-24.04/latest
docker build -t wayoyo/node:latest .
```

---

## Acknowledgments

We would like to express our sincere gratitude to the [webdevops](https://github.com/webdevops) team for their incredible work and enthusiasm in the Docker ecosystem. Their code and innovative approaches have been truly inspiring for this project.

This contribution is not intended to diminish or take credit from their outstanding work, but rather to add more tools and perspectives to the community from our own point of view. We believe in building upon great foundations and contributing back to the open-source ecosystem that has given us so much.

Thank you to the webdevops team for paving the way and inspiring developers like us to create better tools for everyone.

---

## Contributing

Feel free to open issues or submit pull requests to improve this image.

## License

MIT License 