# Dockerized-Web-App-with-Node.js-and-MongoDB
![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/d90314df-5ef8-40b2-9edc-760e465b6d6f)


In software development, it’s important to have a project that works the same everywhere, whether we’re making it, testing it, or sharing it with others. That’s where my project, “Dockerized Full-Stack Application with Node.js and MongoDB,” comes in. It uses Docker to make sure everything runs just right. The front part of the app, where users click and interact, is made using simple tools like HTML5 and JavaScript. 
The behind-the-scenes part is run by Node.js. All the data? It’s saved in a database called MongoDB. Plus, I added MongoExpress, which lets us see and organize the data easily. So, this whole setup makes making and using the app efficient. It’s a simple yet strong web project that brings many benefits. Have a look!

## Components and Interactions:

### Frontend:
- Developed using HTML5 and JavaScript.
- Accessible via localhost:3000/my-app.

### Backend:
- Powered by Node.js.
- Facilitates communication between the frontend and MongoDB.

### MongoDB:
- Used MongoDB for data storage.
- Interacts seamlessly with the backend.

### MongoExpress:
- Incorporated for visual data management.
- Accessible at localhost:8081/db/my-db.

### Docker:
- Employed to containerize both MongoDB and MongoExpress.
- Ensures consistent application performance across different environments.

For a clearer understanding, visualize the data flow: The frontend communicates with the backend, which then interacts with MongoDB. MongoExpress provides a visual interface to MongoDB.

## Directions:

### Step 1:
Begin by visiting Docker Hub. Search for the official images of MongoDB and MongoExpress.

Retrieve the mongo and mongo-express images with:

