# Use official Python image
FROM python:3.12

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Install dependencies (if you have requirements.txt)
# RUN pip install -r requirements.txt 

RUN pip install flask 

# Expose port 5001
EXPOSE 5001

# Command to run the Python app (replace main.py if needed)
CMD ["python", "app.py"]

