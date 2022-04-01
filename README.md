
Re/Create AirFlow:

Ansible push.

```bash
ansible-playbook -i /etc/ansible/inventory/docker-servers -l 10.90.245.100 -v /home/ansible/repo/Ansible/Airflow/playbook_install_airflow.yaml -e @/home/ansible/repo/Ansible/Airflow/private/env.yaml --ask-vault-pass
```

Re/Build docker compose.

```bash
docker-compose down
docker volume rm airflow_storage
DOCKER_BUILDKIT=1
docker-compose up --build airflow-init
docker-compose up --build -d
```

Remove docker compose with volumes:

```bash
docker-compose down
# Clear also data volumes
docker-compose down --volumes
```

airflow users create [-h] -e EMAIL -f FIRSTNAME -l LASTNAME [-p PASSWORD] -r
                     ROLE [--use-random-password] -u USERNAME

```bash
./airflow.sh users create -r Admin -e user@domain.com -f user -l name -p secret -u user
```

```bash
# Create symlink
ln -s /home/jenkins/repo/dags/ /opt/airflow/dags_jenkins
# Remove symlink
ulink dags_jenkins
```

Reverse ssh connection using airflow as jump server:

```powershell
ssh -L [local-port]:[mysql-ip]:[mysql-port] [jump-server-user]@[jump-ip] -p [jump-port] -i [key]

ssh -L 3333:10.100.165.10:3306 ansible@airflow.otcf.pl -p 5566 -i "key path"
ssh -L 3333:10.100.160.11:3306 ansible@airflow.otcf.pl -p 5566 -i "key path"
ssh -L 3333:192.168.125.85:3306 ansible@airflow.otcf.pl -p 5566 -i "key path"
```