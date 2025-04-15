# Devops-P1
Simple web application using Flask (a Python web framework), containerizing it with Docker, and deploying it using Terraform on AWS.
Project Overview

Objective: 
Create a simple Flask web application, containerize it with Docker, and deploy it on AWS using Terraform.

Step 1: 
Create a Simple Flask Application

Create a new directory for your project:

bash
Run
Copy code
mkdir flask-docker-terraform
cd flask-docker-terraform

Create a Python virtual environment (optional but recommended):

bash
Run
Copy code
python3 -m venv venv
source venv/bin/activate

Install Flask:
bash
Run
Copy code
pip install Flask

Create a file named app.py:

python
Run
Copy code
from flask import Flask
app = Flask(__name__)
@app.route('/')
def hello():
    return "Hello, World! This is my Flask app running in Docker."

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)

Create a requirements.txt file:

plaintext
Run
Copy code
Flask
Step 2: Create a Dockerfile
Create a file named Dockerfile:
dockerfile
Run
Copy code

# Use the official Python image from the Docker Hub
FROM python:3.9-slim

# Set the working directory
WORKDIR /app

# Copy the requirements file and install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the application code
COPY app.py .

# Expose the port the app runs on
EXPOSE 5000

# Command to run the application
CMD ["python", "app.py"]

Step 3: 
Build and Run the Docker Container

Build the Docker image:

bash
Run
Copy code
docker build -t flask-app .

Run the Docker container:

bash
Run
Copy code
docker run -p 5000:5000 flask-app

Access the application: Open your web browser and go to 
www.localhost:5000/


