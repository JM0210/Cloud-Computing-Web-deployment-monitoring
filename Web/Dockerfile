FROM python:3.9-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
COPY . .
EXPOSE 5000
# Using environment variables for MongoDB connection as per your app.py
ENV MONGO_HOST=mongodb
ENV MONGO_PORT=27017
CMD ["python", "app.py"]