# Faro_basic-frontend
<h2>Description</h2>

Faro Basic Frontend App
The Faro Basic Frontend App is a simple web application that integrates with the Grafana Faro Web SDK and Faro Web Tracing to enable observability and monitoring capabilities. This app allows users to submit a form with their name and email, which is then stored in a MongoDB database.


<br />

<h2>Languages and Utilities Used</h2>


- Nodejs Express mongoose
- Grafana Faro

<br />
<h2>Environments and tools Used </h2>


- Ubuntu 22.04-GCP VM
- Grafana Cloud 9.5.3
- Node v20.2.0

<br />

<h2>Documentation and learnings Used</h2>

- Faro documentation: https://grafana.com/docs/grafana-cloud/frontend-observability/faro-web-sdk/components/provided-instrumentations/
- Some documentation on NodeJS: 
- https://nodejs.org/en/docs/guides/getting-started-guide
- https://www.freecodecamp.org/news/build-a-secure-server-with-node-and-express/

<br />

<h2>Scope and exclusions</h2>
This test lab in this guide assumes a working knowledge of standing up a nodejs server for testing purposes.  

<h2>Guidelines</h2>
Before setting up and running the Faro Basic Frontend App, ensure that you have the following:

- Node.js installed on your machine
- MongoDB installed and running

<br />

<h2>Guidelines</h2>

The Faro Basic Frontend App is designed to showcase the integration of the Grafana Faro Web SDK and Faro Web Tracing in a simple web application scenario. Here are some key points about the app and what is being tested:

Form Submission: The app includes a form where users can enter their name and email. When the form is submitted, the data is sent to the server and stored in a MongoDB database using the Mongoose library.

Error Handling: The app also includes a button that intentionally throws an error when clicked. This demonstrates how errors can be captured and reported by the Faro Web SDK, enabling observability into application errors.

Observability and Monitoring: The integration with the Grafana Faro Web SDK allows for observability and monitoring capabilities in the app. It collects and sends telemetry data, including traces and errors, to the specified Faro collector URL for further analysis and visualization.

Tracing Instrumentation: The Faro Web Tracing library is added as an instrumentation to the Faro Web SDK. It automatically traces and instruments network requests, providing visibility into the performance of API calls made by the app.

By running the Faro Basic Frontend App and interacting with it, you can test and observe how the Faro Web SDK captures and reports telemetry data, including form submissions, errors, and network requests.

<h2>Procedure</h2>

Setup a GCP/AWS/Azure VM and run the following to install NodeJS and Npm(Node package manager).  Once installed use npm init to initialize the project and create the package.json file in your directory and npm install express which is the library needed to create the HTTP server.   
<br> <br>
 
```
sudo apt-get update
sudo apt-get install nodejs npm
mkdir test-server
cd test-server
npm init -y
npm install express mongoose
```
<br> <br>

In your test-server directory create two files, index.html and server.js.  Create a subdirectory called public and place the index.html file there.
The index.html code creates a simple web page with a form and a button. The form allows users to enter their name, email, and message. The button displays an alert message when it is clicked. The error button throws a JavaScript error objet when pressed in order to demonstrate how errors can be captured and reported by Faro.

<br> <br>


The server.js code creates a simple Node.js web server that listens on port 3000. The server can handle form submissions and button clicks. The server.js file in the Faro Basic Frontend App is the backend server implementation. It handles incoming requests from the frontend, interacts with the MongoDB database, and performs the necessary operations. Here's a description of what the server.js file does:

Dependencies: The server.js file requires the necessary dependencies. It uses the express library for creating the server, and mongoose for interacting with the MongoDB database.

Server Setup: The file initializes an Express application by calling express() and assigns it to the app constant. It also sets the PORT variable to the provided port number (defaulting to 3000).

Database Connection: The file establishes a connection to the MongoDB database using the mongoose.connect() method. It uses the MongoDB URI (MONGODB_URI) to connect to the database.

Database Schema and Model: The file defines a database schema for the User collection using the mongoose.Schema class. The schema specifies the fields name and email, both of type String. It then creates a User model using mongoose.model().

Middleware Setup: The file sets up middleware for handling incoming requests. It uses express.static() to serve static files from the public directory. It also uses express.urlencoded() middleware to parse incoming request bodies with URL-encoded payloads.

Routes: The file defines the routes and their corresponding handlers.

The GET / route sends the index.html file when the root path is accessed. It uses res.sendFile() to serve the file.

The POST /submit route handles form submissions. It creates a new User instance based on the submitted form data (name and email), saves it to the database using await user.save(), and logs the saved user's name. It then redirects the user back to the root path using res.redirect('/').

Server Start: The file starts the server by calling app.listen() and passing the PORT variable. It also logs a message indicating that the server is running and listening on the specified port.

In summary, the server.js file sets up the backend server using Express, establishes a connection to the MongoDB database, defines routes for handling incoming requests, and performs database operations accordingly. It acts as the bridge between the frontend interface and the database, enabling the storage of user data and handling form submissions.
<br> <br>
