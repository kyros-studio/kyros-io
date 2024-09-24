---
title: "🚧 Kyros Quick-Start Guide"
permalink: /docs/quick-start-guide/
excerpt: "How to quickly install and setup Kyros."
last_modified_at: 2024-09-24T08:48:05-04:00
redirect_from:
  - /setup/
toc: true
---

Kyros is designed to be easy to set up and use, allowing data engineers to deploy, customize, and scale data platforms affordably. Follow this guide to get Kyros up and running quickly.

## Installing Kyros

Kyros can be installed as a Docker-based solution or directly on any affordable hosting platform. You can configure Kyros to include only the components you need, such as Apache Spark, dbt, and Apache Flink.

### Docker-Based Installation

If you prefer to use Kyros with Docker, follow these steps:

1. Clone the [Kyros repository](https://github.com/kyroslabs/kyros-project):

   ```bash
   git clone https://github.com/kyroslabs/kyros-project
   cd kyros-project
   ```

2. Build and run the Kyros Docker containers:

   ```bash
   docker-compose up --build
   ```

3. Kyros should now be running. You can access the various services (like JupyterLab, MinIO, etc.) by navigating to the provided URLs in the terminal output.

   - [JupyterLab](http://localhost:8888)
   - [MinIO](http://localhost:9002)
   - [Apache Spark UI](http://localhost:8080)

For more details on how to customize your deployment, refer to the [Configuration Guide](/docs/configuration/).

### System Requirements

Kyros is designed to run on minimal hardware, but for optimal performance, the following resources are recommended:

- **CPU**: 4+ cores
- **Memory**: 8GB+
- **Storage**: 50GB+ (SSD preferred)

### Configuration

Kyros can be customized via the `docker-compose.yml` file. You can enable or disable components like Apache Spark, dbt, and Flink as needed. Here’s an example of how to configure the environment:

```yaml
services:
  spark-master:
    image: kyroslabs/spark:latest
    ports:
      - "8080:8080"
  jupyterlab:
    image: kyroslabs/jupyterlab:latest
    environment:
      - JUPYTER_TOKEN=kyros
```

### Hosting Kyros on a Cloud Provider

1. Spin up a new **cloud instance** from your preferred cloud provider.
2. SSH into your instance and install Docker:

   ```bash
   sudo apt update
   sudo apt install docker docker-compose
   ```

3. Clone the Kyros repository and follow the same steps outlined above for Docker installation.

## Updating Kyros

To update Kyros to the latest version, you can pull the latest changes from the repository and rebuild the Docker containers:

```bash
git pull origin main
docker-compose up --build
```

## Customizing Kyros

Kyros is fully customizable. You can add, remove, or modify services in the `docker-compose.yml` file. Some of the key components you can customize:

- **Apache Spark** for large-scale data processing
- **dbt** for building data pipelines and transformations
- **Apache Flink** for real-time stream processing
- **MinIO** for S3-compatible object storage

Refer to the [Customization Guide](/docs/customization/) for more details on configuring each service.

## Troubleshooting

If you encounter issues, please check the logs for the service in question. For example, to view the logs for the **Spark Master**:

```bash
docker-compose logs spark-master
```

You can also check the [Kyros GitHub Issues](https://github.com/kyroslabs/kyros-project/issues) for known issues and troubleshooting tips.

---

That’s it! You should now have Kyros running on your local machine or hosting platform. For more advanced setup options, refer to the [Advanced Configuration Guide](/docs/advanced-configuration/).
