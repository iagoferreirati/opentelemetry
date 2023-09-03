# OpenTelemetry Setup Guide

This guide will walk you through the process of setting up OpenTelemetry for your project.

## Prerequisites

Before you begin, make sure you have the following prerequisites in place:

1. Kubernetes cluster up and running.
2. `kubectl` command-line tool installed and configured to interact with your cluster.
3. Cert-manager installed on your cluster (if not already done).

### Install Cert-manager

To install Cert-manager on your Kubernetes cluster, run the following command:

```shell
kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.12.0/cert-manager.yaml
```

### Install OpenTelemetry Operator

To install the OpenTelemetry Operator, run the following command:


```shell
kubectl apply -f https://github.com/open-telemetry/opentelemetry-operator/releases/latest/download/opentelemetry-operator.yaml
```

### Create OpenTelemetry Deployment

If you're using Kinesis, it's likely you need to set up HTTPS for your OpenTelemetry instance, especially if you're receiving logs from CloudWatch Metrics Streams. Here's how you can do it:

```shell
kubectl apply -f deployment.yaml
```

### Setting Up HTTPS with Certbot (for use with Kinesis)
If you're using Kinesis and need to set up HTTPS for your OpenTelemetry instance, you can use Certbot to generate a certificate. Here's how you can do it:

Replace `your_domain_name_here` with your desired domain name.
Run the following command to generate a certificate:

```shell
certbot certonly --standalone -d your_domain_name_here
```