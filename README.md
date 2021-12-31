# dockerSwarmPHPMYSQL
**penerapan docker swarm pada multi container menggunakan docker compose dan haproxy**

use docker stack as an orchestrator to run these containers
```
docker stack deploy --compose-file docker-compose.yml simple-crud
```

import table manual on docker swarm node worker (container db)
```
docker exec -ti <name_container_db> bash
```
```
apt update && apt install nano
```
copy from db/employees.sql to (container db):
```
nano docker-entrypoint-initdb.d/employees.sql
```

running HAProxy docker to as proxy or load balancer
```
docker run -dit --name haproxy -v $(pwd):/usr/local/etc/haproxy:ro --network simple-crud_afif-net -p 80:81 haproxy:lts-alpine
```
