# MongoDB & Redis Environment (Docker Compose)

[🇷🇺 Russian Version](../rus/mongo-and-redis.md)

---

This configuration is designed to quickly spin up a local environment with MongoDB and Redis databases required for the parser's operation.

### Prerequisites
Make sure you have the following tools installed on your system:
* **Docker**
* **Docker Compose**
> [!WARNING]
> **Security Notice:** Before running the containers, make sure to open the `docker-compose.yml` file and update the default credentials in the `environment` section to your own:
> * `MONGO_INITDB_ROOT_USERNAME` (MongoDB root username)
> * `MONGO_INITDB_ROOT_PASSWORD` (MongoDB root password)
>
> Additionally, remember to change the Redis password in the command line: `--requirepass your_new_password`. Never leave default passwords unchanged if you plan to use these databases outside your local machine!

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
If your parser script runs directly on the host machine (outside Docker), use the following connection strings:

* **MongoDB URI:** `mongodb://root:secretpassword@localhost:27017/`
* **Redis URL:** `redis://:redispassword@localhost:6379`

### Container Management
* **Check operational status:** `docker compose ps`
* **View real-time database logs:** `docker compose logs -f`
* **Stop and remove containers:** `docker compose down`
