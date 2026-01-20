# Dify Container Names Summary

All containers in the Docker Compose setup have been configured with explicit container names using the "dify-" prefix. This ensures easy identification and management of containers.

## Container Names Configured

### Core Services
- **API Server**: `dify-docker-server` (port 5051:5001)
- **Web Frontend**: `dify-web` (port 2881:3000)
- **Worker (Celery)**: `dify-worker`
- **Worker Beat (Scheduler)**: `dify-worker-beat`

### Database & Cache
- **PostgreSQL**: `dify-db-postgres`
- **MySQL**: `dify-db-mysql`
- **Redis**: `dify-redis`

### Infrastructure & Proxy
- **Nginx (Reverse Proxy)**: `dify-nginx` (ports 2081:80, 2443:443)
- **SSRF Proxy**: `dify-ssrf-proxy`
- **Sandbox**: `dify-sandbox`
- **Plugin Daemon**: `dify-plugin-daemon` (port 5003:5003)
- **Init Permissions**: `dify-init-permissions`
- **Certbot**: `dify-certbot` (optional, profile: certbot)

### Vector Databases
- **Weaviate**: `dify-weaviate` (profile: weaviate)
- **OceanBase**: `oceanbase` (profile: oceanbase)
- **SeekDB**: `seekdb` (profile: seekdb)
- **Qdrant**: `dify-qdrant` (profile: qdrant)
- **PGVector**: `dify-pgvector` (profile: pgvector)
- **Pgvecto-rs**: `dify-pgvecto-rs` (profile: pgvecto-rs)
- **Vastbase**: `dify-vastbase` (profile: vastbase)
- **Chroma**: `dify-chroma` (profile: chroma)
- **Couchbase**: `couchbase-server` (profile: couchbase)
- **IRIS**: `dify-iris` (profile: iris)
- **Oracle**: `dify-oracle` (profile: oracle)
- **OpenSearch**: `dify-opensearch` (profile: opensearch)
- **OpenSearch Dashboards**: `dify-opensearch-dashboards` (profile: opensearch)
- **Milvus (Etcd)**: `dify-etcd` (profile: milvus)
- **Milvus (MinIO)**: `dify-minio` (profile: milvus)
- **Milvus (Standalone)**: `dify-milvus` (profile: milvus)
- **MyScale**: `dify-myscale` (profile: myscale)
- **Matrixone**: `dify-matrixone` (profile: matrixone)

### Search & Analytics
- **Elasticsearch**: `dify-elasticsearch` (profile: elasticsearch, elasticsearch-ja)
- **Kibana**: `dify-kibana` (profile: elasticsearch)

### Data Processing
- **Unstructured**: `dify-unstructured` (profile: unstructured)

## Port Configuration

### Main Access Ports
- **HTTP**: 2081 (nginx)
- **HTTPS**: 2443 (nginx)
- **Web Frontend**: 2881
- **API**: 5051
- **Plugin Daemon**: 5003

### Docker Usage

To start Dify with the default configuration:
```bash
docker compose up -d
```

To list all running containers:
```bash
docker ps
```

To access specific container logs:
```bash
docker logs dify-docker-server
docker logs dify-web
docker logs dify-nginx
```

To stop a specific container:
```bash
docker stop dify-docker-server
```

## Notes
- Some services use profiles (e.g., `weaviate`, `milvus`, `opensearch`) and require the `--profile` flag to start
- The `dify-` prefix makes it easy to identify all Dify-related containers with `docker ps | grep dify-`
- Container names are configured in [docker-compose.yaml](docker-compose.yaml)
- Port mappings are configured in both `.env` and `docker-compose.yaml`
