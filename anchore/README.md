# Anchore Quickstart
The vulnerable image I'm analyzing is `vulnerables/web-dvwa:latest`

```bash
# Setup
curl -O https://engine.anchore.io/docs/quickstart/docker-compose.yaml
docker-compose up -d
docker-compose exec api anchore-cli system status
docker-compose exec api anchore-cli system feeds list
docker-compose exec api anchore-cli system wait

# Analyze image
docker-compose exec api anchore-cli image add vulnerables/web-dvwa
docker-compose exec api anchore-cli image wait vulnerables/web-dvwa
docker-compose exec api anchore-cli image content vulnerables/web-dvwa os
docker-compose exec api anchore-cli image vuln vulnerables/web-dvwa all
docker-compose exec api anchore-cli evaluate check vulnerables/web-dvwa
```


## References
https://engine.anchore.io/docs/quickstart/