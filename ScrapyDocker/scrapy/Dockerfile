# As Scrapy runs on Python, I choose the official Python 3 Docker image.
FROM python:3
ENV PYTHONDONTWRITEBYTECODE=1
ENV PYTHONUNBUFFERED=1
# Set the working directory to /usr/src/app.
WORKDIR /code
 
# Copy the file from the local host to the filesystem of the container at the working directory.
COPY requirements.text /code/
 
# Install Scrapy specified in requirements.txt.
RUN pip install -r requirements.text
 
# Copy the project source code from the local host to the filesystem of the container at the working directory.
COPY . /code/
 
