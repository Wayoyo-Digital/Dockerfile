# Explanation of the pdf2HtmlEx Dockerfile for Ubuntu 24.04

This Dockerfile creates a container image that includes the `pdf2htmlEX` utility on top of an Ubuntu 24.04-based Python environment. The image is designed not only for PDF to HTML conversion, but also as a development container for Python projects using frameworks like Flask or FastAPI.

## Dockerfile Overview

### 1. Multi-Stage Build

- **Stage 1:**  
  Starts from `pdf2htmlex/pdf2htmlex:0.18.8.rc2-master-20200820-ubuntu-20.04-x86_64`.  
  In this stage, all the required shared libraries for `pdf2htmlEX` are copied into a temporary directory. This ensures that all dependencies are available for the final image.

- **Stage 2:**  
  Uses `wayoyo/python:latest` as the base image, which is suitable for Python development.  
  The `pdf2htmlEX` binary, its resources, and the previously extracted libraries are copied into their appropriate locations in the new image.

### 2. Python Development Ready

The final image is based on a Python environment, making it ideal for developing and running Python applications. You can easily install Flask, FastAPI, or other Python frameworks and libraries as needed.

### 3. Use Cases

- **PDF to HTML Conversion:**  
  Use the included `pdf2htmlEX` tool to convert PDF documents to HTML format.

- **Python Web Development:**  
  The image is ready for development with Python web frameworks such as Flask or FastAPI. This makes it suitable for building web APIs or applications that process or serve converted HTML content.

### 4. How It Works

- Extracts all necessary libraries from the original `pdf2htmlEX` image to ensure compatibility.
- Copies the `pdf2htmlEX` binary and its resources to the new image.
- Provides a Python environment for further development.

### 5. Getting Started

To use this container for development:

1. **Build the image:**
   ```
   docker build -t pdf2htmlex-dev .
   ```

2. **Run the container with your project:**
   ```
   docker run -it -v $(pwd):/app pdf2htmlex-dev bash
   ```

3. **Install Flask or FastAPI as needed:**
   ```
   pip install flask fastapi uvicorn
   ```

4. **Develop your Python application using Flask or FastAPI, and use `pdf2htmlEX` as needed within your code or scripts.**

---

This container is ideal for developers who need both PDF to HTML conversion capabilities and a modern Python development environment, especially for building web services or APIs with Flask or FastAPI.


