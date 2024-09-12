# Stage 1: Build Stage
FROM python:3.11-slim AS build

# Set the working directory
WORKDIR /app

# Copy the requirements file
COPY requirements.txt .

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code
COPY . .

# Stage 2: Final Stage
FROM python:3.11-slim

# Set the working directory
WORKDIR /app

# Copy only the necessary files from the build stage
COPY --from=build /app /app

# Install Gunicorn
RUN pip install gunicorn

# Expose port 5000
EXPOSE 5000

# Run the application using Gunicorn
CMD ["gunicorn", "-b", "0.0.0.0:5000", "--workers", "4", "--threads", "8", "encrypt:app"]
