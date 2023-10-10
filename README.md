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

`docker pull mongo`

`docker pull mongo-express`

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/ff39fd3e-f7f5-45e9-9b49-955c4503caae)

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/c958e4da-ecf3-4eae-8cf4-b190b68bc6db)

Verify the local presence of these images using:

`docker images`

Upon success, you'll see the listed images.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/85cc04fb-8a9c-4c06-bd47-4c6ac63400df)

### Step 2:
To make MongoDB accessible for the app and link Mongo Express with MongoDB, run both containers. First, interlink the images through a Docker network:

`docker network create mongo-network`

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/ded3d44a-880a-4ac3-9a0e-347c4e6a2d62)

Confirm its creation:

`docker network ls`
![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/d1699945-0d86-45b2-adab-9215af1838b3)

### Step 3:
To run Mongo Containers:

`docker run -p 27017:27017 -d -e MONGO_INITDB_ROOT_USERNAME=admin -e MONGO_INITDB_ROOT_PASSWORD=password --name MongoDB --net mongo-network mongo`

The above command launches a Mongo container with the specified port and credentials, operating within the earlier created Mongo-network.
![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/fc979bca-ad27-4820-9d53-237e1c774c3c)


Verify success using the log command:

`Docker logs 3df02354fa9580e2b6fa9e3282f55e46d278ef259ca17bacb78936f77b4b3ac4`

Finally, kickstart Mongo Express to auto-connect to MongoDB on initialization.

