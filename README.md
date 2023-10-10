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

### Step 4: Setting Up Mongo Express

Execute the following docker run command for express:

`docker run -d -p 8081:8081 -e ME_CONFIG_MONGODB_ADMINUSERNAME=admin -e ME_CONFIG_MONGODB_ADMINPASSWORD=password --net mongo-network --name mongo-express -e ME_CONFIG_MONGODB_SERVER=mongodb mongo-express`

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/5734f7f7-5959-4c40-9682-55319182d7c3)

This command allows Mongo-express to connect with the MongoDB container. To confirm the successful execution, inspect the logs:

`docker logs dd54e7f58a9585222e993ceb854519821d8ee715f019c08f36fcea9996861460`

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/1f6f2613-3094-45ff-b39a-84ce3e43c004)


Upon accessing http://localhost:8081/, you should see the Mongo-express interface.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/84d3294a-0157-4c9b-ba79-bff419f83684)


### Troubleshooting Tip:
If you face difficulties logging into MongoDB using the initialized credentials, check the mongo-express logs:

`Docker logs 4883726ec7e4d806863ceeffe06d778d2be008a0ad45a1d11dbbe936268e9380`

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/c6a3f7b5-446b-4fe4-87be-e911c10b3d18)

The part that says: **basicAuth credentials are.......**

Any discrepancies in the passwords should be addressed, and on rectifying, you should gain access to the mongo-express page at http://localhost:8081/.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/3f6f90bf-5da1-44ad-b30e-632ba137f6b8)

The images show the databases that already exist by default. Using the UI and the menu “create Database,” we can create our own database.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/6a4aa01a-f616-4685-b1fc-1ed3c16413c3)

We can connect to this database from nodejs.


### Step 5: Connecting Node.js to the Database

Upon accessing the user account created on mongo-express, it will initially appear empty. Visit http://localhost:3000/ and make the necessary edits.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/71e1e944-5731-4464-8e46-f92f2852da5c)

Let’s connect nodejs to the database. You can find the code for nodejs [here](https://pages.github.com/](https://gitlab.com/nanuchi/techworld-js-docker-demo-app/-/blob/702626e30bbde652f06b4d31afdd284652cb15a9/app/server.js).

-In mongo-express UI - create a new database "my-db"
-in mongo-express UI - create a new collection "users" in the database "my-db"
-start node server using the command below:

`npm install`

`node server.js`

Navigate to:
http://localhost:3000/
Make edits:

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/5ada344c-492b-4545-94ef-a988c1c11646)


Revisiting the mongo-express page will display the new database entries.

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/568c719e-8c9e-432f-be78-8488482263a8)

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/20249f40-ab38-4ece-98f7-63f618ba88e8)

To view the log activity, use:

`docker logs cb34f6110ecd`

(Note: 'cb34f6110ecd' represents my container ID)

A snippet of the log activity should display as follows:

![image](https://github.com/OluwaTossin/Dockerized-Web-App-with-Node.js-and-MongoDB/assets/121174963/e56f87bc-d617-4306-8090-aaaaa75a83be)


Upon completion, you'll have a Node.js application with MongoDB persistence. Additionally, the Mongo UI, both encapsulated within Docker containers, offers a perfect representation of local development using Docker.

This setup exemplifies the efficient and streamlined local development potential offered by Docker containers.
