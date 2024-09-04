# # Use the official Python image from the Docker Hub
# FROM python:3.11-slim

# # Set the working directory in the container
# WORKDIR /app

# # Copy the requirements.txt file into the container
# COPY requirements.txt .

# # Install the Python dependencies
# RUN pip install --no-cache-dir -r requirements.txt

# # Copy the rest of your application code into the container
# COPY . .

# # Expose the port that the application will run on
# EXPOSE 5000

# # Command to run the application
# CMD ["python", "app.py"]



# # Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set the working directory to /app
WORKDIR /app

# Copy the current directory contents into the container at /app
COPY . .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Install Gunicorn
RUN pip install gunicorn

# Make port 5000 available to the world outside this container
EXPOSE 5000

# Run app.py using Gunicorn, which is more suitable for production
CMD ["gunicorn", "-b", "0.0.0.0:5000", "--workers","4", "--threads","8", "encrypt:app"]
