# Use Python official image
FROM python:3

# Set the working directory in the container
WORKDIR /app

# Copy the dependencies file to the working directory
COPY requirements.txt .

# Install the dependencies
RUN pip3 install -r requirements.txt

# Copy the content of the local src directory to the working directory
COPY . .

# Expose the port on which the app runs
EXPOSE 80

# Command to run the application
CMD ["flask", "run", "--host=0.0.0.0", "--port=80"]
