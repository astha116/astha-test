# NestJS on Azure

## Live URL
https://astha-test1.azurewebsites.net/

## Steps Followed

1. **Created app** using `nest new sample-api`
2. **Dockerized** with custom `Dockerfile`
3. **Created Azure resources** using `az` CLI
4. **Configured GitHub Actions** for CI/CD
5. **Environment variables** configured securely via Azure Portal
6. **Monitoring** enabled via Azure Log Stream
7. Added `/health` endpoint for uptime checks

## Commands

```bash
az group delete --name astha-rg --yes
