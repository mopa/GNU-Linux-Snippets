# Docker Snippets

+ Update all dockers with Watchtower
```bash
docker run --rm --name watchtower -p 8180:8080 -v /var/run/docker.sock:/var/run/docker.sock containrrr/watchtower --run-once --debug --cleanup
```
