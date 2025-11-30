# Huawei Cloud Log Analysis Pipeline

## Description

This project implements a log analysis pipeline on Huawei Cloud. It ingests logs using LTS (Log Tank Service), stores raw log data in OBS (Object Storage Service), processes logs for anomaly detection using MRS (MapReduce Service/Spark), and provides a custom solution for visualizing alerts.

## Architecture

The architecture consists of the following components:

*   **Logs Source:** The origin of the log data.
*   **LTS (Log Tank Service):** Huawei Cloud's managed log collection and ingestion service.
*   **OBS (Object Storage Service):** Huawei Cloud's object storage for storing raw log data.
*   **MRS (MapReduce Service/Spark):** Huawei Cloud's big data processing service used for anomaly detection.
*   **Anomaly Detection Logic:** The Spark job or MapReduce program that identifies anomalies in the log data.
*   **Alert Visualization:** A custom visualization solution for displaying detected anomalies.

```mermaid
graph LR;
    A[Logs Source] --> B(LTS - Log Tank Service);
    B --> C(OBS - Object Storage Service);
    C --> D{MRS - MapReduce Service/Spark};
    D --> E[Anomaly Detection Logic];
    E --> F[Alert Visualization (Custom)];
    subgraph Huawei Cloud
      B
      C
      D
    end
```

## Setup

1.  **Prerequisites:**
    *   Docker
    *   Docker Compose

2.  **Clone the repository:**
    ```bash
    git clone <repository_url>
    cd <repository_directory>
    ```

3.  **Start the services:**
    ```bash
    docker-compose up -d
    ```

4.  **Access the Alert Visualization:**

The Alert Visualization will be available at `http://localhost:8000` after the services are running. It reads mocked Anomaly data from mock_mrs.

## Components

*   **alert_visualization:** A basic Python HTTP server serving a simple HTML page that displays alert data (mocked in this example).  It reads mocked data from `mock_mrs` endpoint.
*   **mock_mrs:** A mocked MRS API that returns dummy anomaly data for testing the `alert_visualization` service.
