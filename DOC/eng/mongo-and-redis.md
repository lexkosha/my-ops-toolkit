# MongoDB & Redis Environment (Docker Compose)

[🇷🇺 Russian Version](../rus/mongo-and-redis.md)

---

This configuration is designed to quickly spin up a local environment with MongoDB and Redis databases required for the parser's operation.

### Prerequisites
Make sure you have the following tools installed on your system:
* **Docker**
* **Docker Compose**

---

### 🔐 Important: Security and the .env File

Storing plain-text passwords directly inside the `docker-compose.yml` file is highly insecure, especially when publishing your project to GitHub. The best practice to secure your credentials is to use environment variables via a `.env` file.

#### Steps to set it up:

1. In the `mongo-and-redis/` directory, create a text file named `.env` right next to `docker-compose.yml`.
2. Copy the following lines into it and replace them with your own secure credentials:
   ```env
   MONGO_ROOT_USER=your_root_username
   MONGO_ROOT_PASSWORD=your_secure_password
   REDIS_PASSWORD=your_redis_password
   ```
3. Docker Compose will automatically inject these variables into the configuration upon startup.

> [!WARNING]
> **Warning:** Never commit your `.env` file to a public repository! Make sure to add `.env` to your `.gitignore` file.

---

### Usage Instructions
1. Open your terminal and navigate to the directory containing the configuration file:
   ```bash
   cd ../../mongo-and-redis
   ```
2. Start the containers in the background:
   ```bash
   docker compose up -d
   ```

### Connection Settings (for the parser)
If your parser script runs directly on the host machine (outside Docker), use the credentials you defined in your `.env` file to connect:

* **MongoDB URI:** `mongodb://<MONGO_ROOT_USER>:<MONGO_ROOT_PASSWORD>@localhost:27017/`
* **Redis URL:** `redis://:<REDIS_PASSWORD>@localhost:6379`

### Container Management
* **Verify variable substitution (without starting):** `docker compose config`
* **Check operational status:** `docker compose ps`
* **View real-time database logs:** `docker compose logs -f`
* **Stop and remove containers:** `docker compose down`
