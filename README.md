# GenAI-Week10
A docker environment to host n8n
## Quick Start

### Prerequisites
- Docker and Docker Compose installed on your system
- Port 5678 available (or configure a different port in `.env`)

### Setup Instructions

1. **Clone the repository and navigate to the project directory:**
   ```bash
   cd /workspaces/GenAI-Week10
   ```

2. **Create environment configuration:**
   ```bash
   cp .env.example .env
   ```
   Edit `.env` to customize settings like host, port, and protocol as needed.

3. **Start n8n with Docker Compose:**
   ```bash
   docker-compose up -d
   ```

4. **Access n8n:**
   - Open your browser and navigate to `http://localhost:5678`
   - The n8n interface will be available after the container starts

### Useful Commands

```bash
# View logs
docker-compose logs -f n8n

# Stop n8n
docker-compose down

# Remove volumes (caution: deletes stored workflows and data)
docker-compose down -v

# Restart n8n
docker-compose restart n8n
```

### Configuration

Edit the `.env` file to customize:
- `N8N_HOST`: The hostname for n8n (default: `localhost`)
- `N8N_PORT`: The port n8n runs on (default: `5678`)
- `N8N_PROTOCOL`: Protocol to use (default: `http`, set to `https` for production)
- `WEBHOOK_URL`: URL for webhook triggers

### Database

The current setup uses **SQLite** for data persistence, which is suitable for development and small deployments. Data is stored in the `n8n_data` volume.

To upgrade to PostgreSQL for production:
1. Update the environment variables in `.env` with PostgreSQL credentials
2. Add a PostgreSQL service to `docker-compose.yml`
3. Restart the containers

### Data Persistence

Workflows, credentials, and settings are persisted in the `n8n_data` Docker volume. This volume is automatically created and managed by Docker.

### Further Customization

For additional customization options, refer to the [n8n documentation](https://docs.n8n.io/).