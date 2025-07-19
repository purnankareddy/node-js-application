
Project Structure

root/
├── patient-service/
│   ├── patient-service.js
│   ├── package.json
│   └── Dockerfile
├── appointment-service/
│   ├── appointment-service.js
│   ├── package.json
│   └── Dockerfile
Steps to Build and Run

1. Prepare Each Service

In both patient-service and appointment-service folders:
Add package.json with dependencies:
{
  "name": "service-name",
  "version": "1.0.0",
  "main": "patient-service.js", 
  "dependencies": {
    "express": "^4.18.2"
  }
}
Create Dockerfile:
# Use Node.js base image
FROM node:18
WORKDIR /app
COPY . .
RUN npm install
EXPOSE 3000  
CMD ["node", "patient-service.js"] 
2. Build Docker Images

Run in each service directory:
docker build -t patient-service         
run the command in patient-service/
docker build -t appointment-service      
run the above command in appointment-service/

3. Run Containers

Start containers:
docker run -p 3000:3000 patient-service
docker run -p 3001:3001 appointment-service



Checking codespce env : statis check:
 curl localhost:3001/health
Appointment:: http://localhost:3001/
