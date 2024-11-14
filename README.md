
# Project Documentation

This repository contains the setup for a development environment utilizing Docker to orchestrate MongoDB, Elasticsearch, Kibana, and Elastic Connectors. The configuration enables a seamless setup for data management, indexing, and visualization.

## Project Structure

- **docker-compose.yml**: Defines the Docker services and configurations for MongoDB, Elasticsearch, Kibana, and Elastic Connectors.
- **config.yml**: Configuration file for the Elastic Connectors, specifying connections and authentication to Elasticsearch and MongoDB.

## Requirements

- **Docker** and **Docker Compose** must be installed on your system.

## Getting Started

### 1. Clone the Repository
   ```bash
   git clone https://github.com/youssefaouadni/elastic-search-with-kibana-and-mongo-connectors.git
   cd your-repo
   ```

### 2. Update Environment Variables
   Edit `docker-compose.yml` and `config.yml` to customize credentials and configurations:
   
   - **MongoDB**: Set `MONGO_INITDB_DATABASE`, `MONGO_INITDB_ROOT_USERNAME`, and `MONGO_INITDB_ROOT_PASSWORD`.
   - **Elasticsearch**: Customize `ELASTIC_PASSWORD` and adjust memory allocation if needed.
   - **Elastic Connectors**: Configure `api_key`, `connector_id`, and other connection settings in `config.yml`.

### 3. Start the Services
   ```bash
   docker-compose up -d
   ```

   This command launches all services in detached mode.

### 4. Accessing Services

- **MongoDB**: Available at `localhost:27017`
- **Elasticsearch**: Accessible at `localhost:9200`
- **Kibana**: Reachable via `localhost:5601`

## Configuration Details

- **MongoDB**:
  - Database initialization scripts can be placed in the `mongo-entrypoint` folder.
  - Data volumes are mapped to persist the database state across container restarts.

- **Elasticsearch**:
  - Security and memory configurations are set to optimize single-node performance.
  - Password and API keys are enabled for authentication.

- **Kibana**:
  - Integrates with Elasticsearch and requires the `kibana_system` user for secure access.

- **Elastic Connectors**:
  - Uses the `config.yml` file to define connections to data sources.

## Networking

The services are connected via an internal Docker bridge network named `mongodb_network`, enabling isolated and secure communication between the containers.

## Volumes

Data persistence is achieved using Docker volumes:
- MongoDB data: `./data:/data/db`
- Elasticsearch data: `./elastic-data:/usr/share/elasticsearch/data`
- Elastic Connectors config: `./connectors-config:/config`

## Security

The services use basic security mechanisms including environment variables for sensitive information and an internal Docker network to restrict external access.

## Troubleshooting

- **Service Logs**: Run `docker-compose logs <service_name>` to view logs for each container (e.g., `mongodb`, `elasticsearch`, `kibana`, `elastic-connectors`).
- **Restarting Containers**: If a configuration change is made, restart the containers with `docker-compose restart <service_name>`.

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

---

