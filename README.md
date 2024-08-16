# node-docker

This is a simple Node.js application that can be containerized using Docker. The Dockerfile is set up to use a Node.js base image, install dependencies, and run the server.

## Prerequisites

Before starting, ensure you have the following installed:

- [Docker](https://www.docker.com/)
- [Node.js](https://nodejs.org/) (Optional, only needed for local development)

## Project Structure

```
.
├── Dockerfile          # Docker setup
├── package.json        # Node.js dependencies
├── server.js           # Main application file (Node.js server)
├── app.js 
└── README.md           # Project documentation
```

### Main Components

1. **`package.json`**: Contains the project’s metadata and dependencies for the Node.js application.
2. **`server.js`**: This is the main file where the Node.js server logic resides. The server listens on port `8080` by default.

## Getting Started

### 1. Clone the Repository

```bash
git clone git@github.com:sujaybn/node-docker.git
cd node-docker
```

### 2. Running the Node.js Application Locally

If you'd like to run the Node.js application locally (without Docker), you can do the following:

#### Install Dependencies:

Make sure you have Node.js installed, then run:

```bash
npm install
```

#### Start the Server:

```bash
node server.js
```

By default, the application will be hosted on `http://localhost:8080`.

### 3. Docker Setup

#### Dockerfile Overview

- **Base Image**: The Dockerfile starts with the Node.js `16` base image.
- **App Directory**: Creates a directory `/usr/src/app` inside the container to hold the application code.
- **Install Dependencies**: Copies `package.json` and runs `npm install` to install the dependencies.
- **App Files**: Copies the rest of the application files into the container.
- **Expose Port**: Exposes port `8080` so that the application can be accessed externally.
- **Start Command**: Runs the Node.js server using `node server.js`.

### 4. Build the Docker Image

To build the Docker image for the application, run the following command in the project directory:

```bash
docker build -t node-app .
```

This will create a Docker image named `node-app` based on the `Dockerfile`.

### 5. Running the Docker Container

After building the Docker image, you can run the container with the following command:

```bash
docker run -p 8080:8080 node-app
```

This maps port `8080` on your local machine to port `8080` on the Docker container. You can then access the application at `http://localhost:8080`.

### 6. Accessing the Application

Once the container is running, open your browser and go to:

```
http://localhost:8080
```

You should see the output from your Node.js application.

## Conclusion

This simple Node.js application can be run locally or inside a Docker container. The Dockerfile provided ensures that the application is containerized and easy to deploy. You can customize the application by modifying the `server.js` file or the `package.json` dependencies.
