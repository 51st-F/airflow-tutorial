# Airflow-Tutorial

Use my personal laptop to develop ETL pipeline on Win11.

## Get Started

- Create `.env` file

```
AIRFLOW_UID=50000
```

- Download official yaml file [Airflow 2.3.3](https://airflow.apache.org/docs/apache-airflow/2.3.3/docker-compose.yaml)

- Create blank folder `dags`, `logs`, `plugins`

### Your Start-Up Tree 

```
.
│  .env
│  docker-compose.yaml
│  README.md
├─dags
├─logs
└─plugins
```

- Initialize the database

```
$ docker compose up airflow-init
```

- Images pulled after airflow-init as below

```
$ docker image ls
REPOSITORY                   TAG        IMAGE ID       CREATED        SIZE
redis                        latest     eca1379fe8b5   35 hours ago   117MB
postgres                     13         ab3945c8cf71   7 days ago     374MB
apache/airflow               2.3.3      eb63ad63a57f   9 months ago   1.09GB
```
- Running airflow

```
$ docker compose up -d
```

- Default running container as below

```
$ docker ps -a
CONTAINER ID   IMAGE                  COMMAND                  CREATED         STATUS                     PORTS                    NAMES
4698cab95d49   apache/airflow:2.3.3   "/usr/bin/dumb-init …"   5 minutes ago   Up 5 minutes (healthy)     8080/tcp                 airflow-tutorial-airflow-triggerer-1
a7fbadfa8660   apache/airflow:2.3.3   "/usr/bin/dumb-init …"   5 minutes ago   Up 5 minutes (healthy)     0.0.0.0:8080->8080/tcp   airflow-tutorial-airflow-webserver-1
79603aae15e4   apache/airflow:2.3.3   "/usr/bin/dumb-init …"   5 minutes ago   Up 5 minutes (healthy)     8080/tcp                 airflow-tutorial-airflow-worker-1
08d65eca29b6   apache/airflow:2.3.3   "/usr/bin/dumb-init …"   5 minutes ago   Up 5 minutes (healthy)     8080/tcp                 airflow-tutorial-airflow-scheduler-1
a18ff61bf7c2   apache/airflow:2.3.3   "/bin/bash -c 'funct…"   5 minutes ago   Exited (0) 5 minutes ago                            airflow-tutorial-airflow-init-1
254391524f9d   redis:latest           "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes (healthy)     6379/tcp                 airflow-tutorial-redis-1
c99e4eb290b4   postgres:13            "docker-entrypoint.s…"   5 minutes ago   Up 5 minutes (healthy)     5432/tcp                 airflow-tutorial-postgres-1
```

> Now you can access into [Airflow Login Page](http://localhost:8080/)
>> Default username/password: `airflow`