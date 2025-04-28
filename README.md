# Chat App

This project is a real-time, multi-user chat application designed around a single, shared chat room where users can communicate with each other instantly.

## Features

* **User Authentication:** Allows users to register new accounts and log in.
* **Single Chat Room Dashboard:** A central dashboard where multiple logged-in users can access and participate in the chat.
* **Real-time Messaging:** Send and receive messages instantly within the chat room using WebSockets.
* **Data Persistence:** Uses a PostgreSQL database to securely store user details and chat messages.
* **Message Queueing:** Leverages Kafka as a stream processing component for reliable and scalable message handling before persistence in the database.
* **Modern Frontend:** A React-based user interface designed for a robust user experience.
* **Backend APIs:** Spring Boot provides REST APIs for frontend-backend interaction and manages the WebSocket server.

## Tech Stack

* Java Spring Boot
* React
* PostgreSQL
* Kafka
* Docker
* Docker Compose

## Architecture

The application follows a layered architecture:

* **Frontend:** A React application providing the user interface for login, signup, and the main chat dashboard. The chat dashboard utilizes WebSockets for real-time message exchange.
* **Backend:** Consists of Java Spring Boot applications.
    * Handles REST APIs for user authentication and data fetching.
    * Manages the WebSocket server for real-time communication.
    * Includes a Kafka **Producer** component responsible for sending incoming messages to the Kafka stream.
    * Includes a separate Kafka **Consumer** service that reads messages from the Kafka stream and performs database (CRUD) operations for message persistence.
* **Kafka:** Serves as a message queue to ensure reliability and handle message processing asynchronously and scalably.
* **Database:** A PostgreSQL database used as the primary data store for user information and chat message history.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

Make sure you have the following installed:

* Docker
* Docker Compose

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/k3vin710/Chat-App.git
    ```

2.  **Navigate to the project directory:**

    ```bash
    cd one-room-chat-app
    ```

3.  **Choose your Docker Compose file based on your system architecture:**

    * **For Windows or Linux (non-ARM based systems):**

        ```bash
        cd oneRoomChat-x86
        docker compose up -d
        ```

    * **For macOS (ARM based systems e.g., Mac M1, M2):**

        ```bash
        cd oneRoomChat-ARM
        docker compose up -d
        ```

    * **Alternatively, build containers locally (works on any system with Docker Compose):**

        ```bash
        cd oneRoomChat # Navigate back to the root if you cd'd into x86/ARM
        docker compose up -d
        ```

This will build and start all the necessary services (backend, frontend, database, Kafka, Zookeeper) in the background.

## Usage

Once the containers are running, you can access the application.

1.  Open your web browser and go to `http://localhost:3000` (or the port your frontend is configured on).
2.  **Register** a new user account via the signup page.
3.  **Login** using your registered credentials.
4.  Start chatting in real-time with other users who are logged into the same chat room.
