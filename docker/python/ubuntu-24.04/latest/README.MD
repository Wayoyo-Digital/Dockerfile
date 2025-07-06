# wayoyo/python:ubuntu-24.04-latest

A lightweight Python container based on Ubuntu 24.04, designed for general Python development.

---

## Features

- Based on Ubuntu 24.04
- Python (from official python:bookworm image)
- Includes [oh-my-posh](https://ohmyposh.dev/) for a beautiful and customizable shell prompt
- Includes [macchina](https://github.com/Macchina-CLI/macchina), a fast and minimal system information tool written in Rust (a lightweight alternative to pfetch)
- Exposes port 8000
- Minimal and ready for development

---

## Usage

### Pull the image

```bash
docker pull wayoyo/python:ubuntu-24.04-latest
```

### Basic usage

#### Interactive shell
Run the container with an interactive bash shell:

```bash
docker run -it wayoyo/python:ubuntu-24.04-latest
```

#### Run Python interactively
```bash
docker run -it wayoyo/python:ubuntu-24.04-latest python3
```

### Development workflow

#### Mount your project directory
For development, mount your local project directory to the container's `/app` directory:

```bash
docker run -it -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest
```

#### Run a Python script
```bash
docker run -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest python3 your_script.py
```

#### Development with port mapping
If your Python application serves on port 8000 (or any other port), map it to your host:

```bash
docker run -it -p 8000:8000 -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest
```

### Common use cases

#### Web application development
For web applications that serve on port 8000:

```bash
# Navigate to your project directory
cd /path/to/your/python/project

# Run with port mapping and volume mount
docker run -it -p 8000:8000 -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest

# Inside the container, install dependencies and run your app
pip install -r requirements.txt
python3 app.py
```

#### Package installation and development
```bash
# Run with volume mount for persistent package installation
docker run -it -v $(pwd):/app -v python_packages:/usr/local/lib/python3.11/site-packages wayoyo/python:ubuntu-24.04-latest

# Install packages that will persist in the named volume
pip install requests flask django
```

#### One-off script execution
```bash
# Run a single Python script and exit
docker run --rm -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest python3 script.py
```

### Environment variables

You can pass environment variables to customize the container behavior:

```bash
docker run -it -e PYTHONPATH=/app -e DEBUG=1 -v $(pwd):/app wayoyo/python:ubuntu-24.04-latest
```

### Docker Compose usage

Create a `docker-compose.yml` file for easier development:

```yaml
version: '3.8'
services:
  python-dev:
    image: wayoyo/python:ubuntu-24.04-latest
    ports:
      - "8000:8000"
    volumes:
      - .:/app
    environment:
      - PYTHONPATH=/app
    working_dir: /app
    tty: true
    stdin_open: true
```

Then run:
```bash
docker-compose up -d
docker-compose exec python-dev bash
```

---

## Build locally

If you want to build the image locally:

```bash
git clone <repository-url>
cd Dockerfile/docker/python/ubuntu-24.04/latest
docker build -t wayoyo/python:ubuntu-24.04-latest .
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


