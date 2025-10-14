# # # # Use an official lightweight Python runtime as a parent image
# # # # FROM python:3.9-slim
# # # FROM python:3.11-slim

# # # # Set the working directory in the container to /app
# # # WORKDIR /app

# # # # Copy the requirements file first to leverage Docker's layer caching.
# # # # This way, dependencies are only re-installed if requirements.txt changes.
# # # COPY requirements.txt .

# # # # Install the Python dependencies
# # # RUN pip install --no-cache-dir -r requirements.txt

# # # # Copy the rest of your application's code into the container at /app
# # # COPY . .

# # # # IMPORTANT: Run your setup script to download the necessary fonts for the app to work.
# # # RUN python setup.py

# # # # Make port 8000 available to the world outside this container
# # # EXPOSE 8000

# # # # Define the command to run your app using Flask's built-in server
# # # # This command runs when the container launches.
# # # CMD ["python", "app.py"]



# # # # Use official Python 3.11 slim image as the base
# # # FROM python:3.11-slim

# # # # Set environment variables to prevent Python from writing pyc files and buffer stdout/stderr
# # # ENV PYTHONDONTWRITEBYTECODE=1
# # # ENV PYTHONUNBUFFERED=1

# # # # Set working directory
# # # WORKDIR /app

# # # # Install system dependencies needed for some Python packages
# # # RUN apt-get update && apt-get install -y --no-install-recommends \
# # #     build-essential \
# # #     libglib2.0-0 \
# # #     libsm6 \
# # #     libxext6 \
# # #     libxrender-dev \
# # #     wget \
# # #     && rm -rf /var/lib/apt/lists/*

# # # # Copy only requirements.txt first to leverage Docker caching
# # # COPY requirements.txt .

# # # # Upgrade pip and install Python dependencies
# # # RUN python -m pip install --upgrade pip && \
# # #     pip install --no-cache-dir -r requirements.txt

# # # # Copy the rest of the application
# # # COPY . .

# # # # Run setup script (e.g., to download fonts)
# # # RUN python setup.py

# # # # Expose port 8000
# # # EXPOSE 8000

# # # # Use Flask's built-in server (for development)
# # # CMD ["python", "app.py"]



# # # Use an official lightweight Python runtime as a parent image
# # FROM python:3.9-slim

# # # Set the working directory in the container to /app
# # WORKDIR /app

# # # ✅ THE FIX: Install the missing system dependency for OpenCV using the correct package name
# # # This command must run BEFORE you install or run any Python code that needs it.
# # RUN apt-get update && apt-get install -y libgl1

# # # Copy the requirements file first to leverage Docker's layer caching
# # COPY requirements.txt .

# # # Install the Python dependencies from requirements.txt
# # RUN pip install --no-cache-dir -r requirements.txt

# # # Copy the rest of your application's code into the container
# # COPY . .

# # # Run your setup script to download the necessary fonts.
# # RUN python setup.py

# # # Make port 8000 available to the world outside this container
# # EXPOSE 8000

# # # Use CMD to define the container's startup command
# # # This runs your Flask app when the container starts.
# # CMD ["python", "app.py"]



# # Use an official lightweight Python runtime as a parent image
# FROM python:3.9-slim

# # Set the working directory in the container to /app
# WORKDIR /app

# # ✅ THE FIX: Install all missing system dependencies for OpenCV in one go.
# # libgl1 was for graphics, and libglib2.0-0 is for threading support.
# RUN apt-get update && apt-get install -y libgl1 libglib2.0-0

# # Copy the requirements file first to leverage Docker's layer caching
# COPY requirements.txt .

# # Install the Python dependencies from requirements.txt
# RUN pip install --no-cache-dir -r requirements.txt

# # Copy the rest of your application's code into the container
# COPY . .

# # Run your setup script to download the necessary fonts.
# # RUN python setup.py

# # Make port 8000 available to the world outside this container
# EXPOSE 8000

# # Use CMD to define the container's startup command
# # This runs your Flask app when the container starts.
# CMD ["python", "app.py"]


# Use an official lightweight Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory in the container to /app
WORKDIR /app

# Install all missing system dependencies for OpenCV in one go
RUN apt-get update && apt-get install -y libgl1 libglib2.0-0

# Copy the requirements file first to leverage Docker's layer caching
COPY requirements.txt .

# Install the Python dependencies from requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of your application's code into the container
COPY . .

# Run your setup script to download the necessary fonts
RUN python setup.py

# Make port 8000 available to the world outside this container
EXPOSE 8000

# ✅ THIS IS THE CRITICAL LINE:
# Use CMD to define the container's startup command.
# This runs your Flask app when the container starts.
CMD ["python", "app.py"]