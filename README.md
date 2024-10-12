This repository contains a demonstration of a PostgreSQL database cluster setup. The cluster consists of one master node and three replica nodes, with different configurations for synchronous and asynchronous replication. This setup is ideal for testing high availability and load balancing in a PostgreSQL environment.

## Cluster Configuration

- **Master Node**: 
  - Acts as the primary node that handles all write operations.
- **Replica Nodes**:
  - **Replica 1**: 
    - Synchronous replication and hot standby.
    - Allows read operations.
  - **Replica 2**: 
    - Synchronous replication and hot standby.
    - Allows read operations.
  - **Replica 3**: 
    - Asynchronous replication and for backup only.
    - Not a hot standby (does not allow read operations).

## Automation Scripts

To manage the PostgreSQL cluster easily, two PowerShell scripts are provided:

- **`startup.ps1`**: 
  - This script starts the entire cluster, initializes the master node, and sets up the replicas according to the specified configurations.
  
- **`down.ps1`**: 
  - This script stops the cluster and performs cleanup operations to ensure a clean shutdown of all nodes.

## Prerequisites

- Docker installed on your system.
- PowerShell for running the automation scripts.

## Getting Started

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/omarfarouk311/Database-Replication-Demo.git
   cd Database-Replication-Demo
   ```
   
2. Create `.env` file that contains POSTGRES_PASSWORD=your_password entry.

3. Run the startup.ps1 script to start the PostgreSQL cluster:
    ```powershell
    .\startup.ps1
    ```

4. To stop the cluster, execute the down.ps1 script:
    ```powershell
    .\down.ps1
    ```
## Usage  
  Once the cluster is up and running, you can connect to the master node to perform write operations.
  Read operations can be performed on either of the synchronous replicas (standby1 or standby2).
  The asynchronous replica can be used for backup purposes but will not accept read requests (standby3).
