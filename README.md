# RocketMQ 5.0.1 Kubernetes Deployment

Apache RocketMQ deployment on Kubernetes with dashboard and ACL authentication.

## Quick Start

```bash
# Deploy all components
kubectl apply -f namesrv.yaml
kubectl apply -f config.yaml
kubectl apply -f broker.yaml
kubectl apply -f dashboard.yaml

# Check status
kubectl get pods -n rocketmq

# Access dashboard
kubectl get svc rocketmq-dashboard -n rocketmq
# Use NodePort to access via cluster nodes
```

## Components

- **NameServer**: Service discovery and routing
- **Broker**: Message storage and delivery
- **Dashboard**: Web UI for monitoring and management
- **ACL**: Authentication and authorization

## Access

- **Dashboard**: http://localhost:8080
- **NameServer**: `rocketmq-namesrv.rocketmq.svc.cluster.local:9876`
- **Broker**: `rocketmq-broker.rocketmq.svc.cluster.local:10911`

## Authentication

| User | Password | Role |
|------|----------|------|
| protco | protco123456 | Admin |
| RoketMQ | 12345678 | Limited |

## Configuration

- **Cluster**: rocketmq-cluster
- **Auto Topic Creation**: Enabled
- **File Retention**: 48 hours
- **Memory**: 512MB per service

## Cleanup

```bash
kubectl delete namespace rocketmq
```