## Highly Available Deployment of Redis in Docker, Docker Swarm, and Kubernetes

This repository provides methods to deploy Redis Sentinel using different orchestration tools:

1. **Redis Sentinel in Docker (Single Node)**:
2. **Redis Sentinel in Docker (Three Nodes)**:
3. **Redis Sentinel in Docker Swarm**:
4. **Redis Sentinel in Kubernetes with Helm**:

---
### Redis Sentinel in Docker (Single Node)

1. Use `docker-1-node` folder.
2. Copy the Docker Compose file to your node.
3. Run the following command:

    ```bash
    docker compose -f docker-compose-all-in-1-node.yml up -d
    ```

---
### Redis Sentinel in Docker (Three Nodes)

1. Use `docker-3-node` folder.
2. Copy the Docker Compose file to each node.
3. Run the following command on each node accordingly:

    ```bash
    docker compose -f docker-compose-node1.yml up -d
    ```

---
### Redis Sentinel in Docker Swarm

1. Use `docker-swarm` folder.
2. Copy the Docker Compose file to a node in your Docker Swarm cluster.
3. Run the following command:

    ```bash
    docker stack deploy -c 'docker-compose-swarm.yml' -d redis
    ```

---
### Redis Sentinel in Kubernetes with Helm

1. Add the Redis Helm repository:

    ```bash
    helm repo add bitnami https://charts.bitnami.com/bitnami
    helm repo update
    ```

2. Install the Redis Sentinel:

    ```bash
    helm upgrade --install redis-sentinel bitnami/redis \
        --set global.redis.password=redis \
        --set sentinel.enabled=true \
        --set replica.persistence.size=4Gi \
        --set metrics.enabled=true
    ```
