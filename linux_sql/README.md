**Introduction**

This project is designed to manage and monitor hardware specifications and usage data across multiple Linux hosts. It primarily targets system administrators and IT infrastructure managers who need to keep track of hardware performance and utilization metrics. The project leverages various technologies such as Bash for scripting, Docker for containerization, Git for version control, and PostgreSQL for database management. The main functionalities include collecting hardware specifications, monitoring usage data, and storing this information in a centralized database for analysis and reporting.


**Quick Start**

Follow these steps to quickly get the project up and running:

Start a PostgreSQL instance using the psql_docker.sh script:
./scripts/psql_docker.sh start

Create necessary tables in the database using the ddl.sql script:
psql -h localhost -U postgres -f sql/ddl.sql

Insert hardware specifications data into the database using the host_info.sh script:
./scripts/host_info.sh

Insert hardware usage data into the database using the host_usage.sh script:
./scripts/host_usage.sh

Set up a crontab job to automate the collection of hardware usage data:
crontab -e

Add the following line to the crontab file to schedule the script to run every minute:
* * * * * /path/to/your/scripts/host_usage.sh


**Implementation**
**Architecture**

Scripts

**psql_docker.sh**
This script manages the lifecycle of a PostgreSQL Docker container.
Usage:
./scripts/psql_docker.sh start|stop|create


**host_info.sh**
This script collects and inserts hardware specifications into the database.
Usage:
./scripts/host_info.sh

**host_usage.sh**
This script collects and inserts hardware usage data into the database.
Usage:
./scripts/host_usage.sh

**crontab**
Crontab is used to schedule the host_usage.sh script to run at regular intervals.
Usage:
crontab -e

**queries.sql**
This script contains SQL queries to resolve specific business problems, such as identifying hosts with the highest CPU usage.

**Test**
The Bash scripts and DDL were tested in a controlled environment using test data. The results were validated by checking the correctness of data inserted into the database and ensuring the scripts executed without errors. All tests passed successfully, confirming the scripts' functionality and reliability.

**Deployment**
The application was deployed using the following steps:
1. Version control with Git: All scripts and SQL files are tracked in a Git repository.
2. Docker: PostgreSQL is run within a Docker container to ensure a consistent and isolated environment.
3. Crontab: Automated scheduling of the host_usage.sh script using crontab for continuous data collection.

**Improvements**

Future improvements for the project include:
1. Handling hardware updates dynamically to reflect changes without manual intervention.
2. Enhancing the user interface for better data visualization and reporting.
3. Adding more detailed logging and error handling to improve script robustness.
