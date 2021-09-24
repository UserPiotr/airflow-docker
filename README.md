```bash
docker-compose up --build airflow-init
docker-compose up --build -d
```

airflow users create [-h] -e EMAIL -f FIRSTNAME -l LASTNAME [-p PASSWORD] -r
                     ROLE [--use-random-password] -u USERNAME

```bash
./airflow.sh users create -r Admin -e user@domain.com -f user -l name -p secret -u user
```