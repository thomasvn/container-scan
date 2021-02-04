# Docker Scan

## Quickstart
The vulnerable image I'm analyzing is `vulnerables/web-dvwa:latest`

```bash
docker scan vulnerables/web-dvwa
docker scan --file docker-vulnerable-dvwa/Dockerfile vulnerables/web-dvwa
docker scan --dependency-tree vulnerables/web-dvwa
```


## Details
- checks dependencies (packages/binaries) for known vulnerabilities (vuln db)
- defaults to the Snyk security engine
- scans images pushed to DockerHub
- requires DockerHub login


## References
- https://docs.docker.com/engine/scan/
- https://hub.docker.com/r/vulnerables/web-dvwa
- https://support.snyk.io/hc/en-us/articles/360003915918-How-Snyk-Container-works
- https://snyk.io/blog/10-docker-image-security-best-practices/