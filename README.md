# Project: Basic Flask Server in Docker Container on EC2

This project demonstrates how to create a basic Python server using Flask, containerize it with Docker, and host it on an EC2 instance. The server will simply respond with "Hello, World" to incoming requests.

## Files Used:
- **app.py**: Contains the Python code for the Flask server.
- **Dockerfile**: Specifies instructions for building the Docker container.
- **requirement.txt**: Lists the Python dependencies required for the project.

## Steps:

### 1. Setting up Flask Server:

- Create a file named `app.py`.
- Copy and paste the following code into `app.py`:

```python
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World'

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```

### 2. Creating Dockerfile:

- Create a file named `Dockerfile`.
- Copy and paste the following code into `Dockerfile`:

```Dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirement.txt requirement.txt
RUN pip install -r requirement.txt

COPY . .

CMD [ "python", "app.py" ]
```

### 3. Defining Python Dependencies:

- Create a file named `requirement.txt`.
- Add the following line to `requirement.txt`:

```
Flask==3.0.2
```

### 4. Building Docker Image:

- Open terminal and navigate to the project directory.
- Execute the following command to build the Docker image:

```
docker build -t flask-server .
```

### 5. Running Docker Container Locally:

- Once the image is built, run the Docker container using the following command:

```
docker run -d -p 5000:5000 flask-server
```

### 6. Hosting on EC2:

- Launch an EC2 instance with Docker installed.
- Copy your Docker image to the EC2 instance.
- Run the Docker container on the EC2 instance, exposing port 5000.

### 7. Accessing Flask Server:

- Open a web browser.
- Navigate to `http://your_ec2_instance_public_ip:5000/`.
- You should see "Hello, World" displayed on the page.

---

This README provides a step-by-step guide to create a basic Flask server,
