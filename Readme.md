# NestJS on Azure

## Live URL
https://astha-test2.azurewebsites.net/

## Steps Followed

1. **Created app** using `nest new sample-api`
2. **Dockerized** with custom `Dockerfile`
3. Tested Docker image locally. It was able to serve request.
<img width="1727" alt="image" src="https://github.com/user-attachments/assets/2556a20e-3a4d-4b5d-a2c7-e59615e88e5e" />
4. Pushed Docker Image to Dockerhub.
5. **Created Azure resources** using `az` CLI

```
az group create --name astha-rg --location eastus
az appservice plan create --name astha-plan --resource-group nastha-rg --is-linux --sku B1

# Create web app
az webapp create --resource-group astha-rg \
  --plan astha-plan \
  --name astha-test2 \
  --deployment-container-image-name asthajain/nestjs-azure:latest
```
  
5. **Configured GitHub Actions** for CI/CD and added variablised secrets in github secrets.
6. **Environment variables** configured securely via Azure Portal
7. **Monitoring** enabled via Azure Log Stream

<img width="1728" alt="image" src="https://github.com/user-attachments/assets/ed1e471e-82bb-4900-a088-ae4a91f586f7" />

<img width="1719" alt="image" src="https://github.com/user-attachments/assets/10ff75b2-d6c9-4a0f-ad4b-9ab9e33f09a3" />

## 🛠️ Troubleshooting

| Problem                              | Solution                                                                 |
|--------------------------------------|--------------------------------------------------------------------------|
| `npm: command not found`             | Install Node.js via Homebrew or nvm                                      |
| `MissingSubscriptionRegistration`    | Run `az provider register --namespace Microsoft.Web`                     |
| App shows 502 / doesn't load         | Ensure Dockerfile is correct and Nest is listening on `0.0.0.0`          |
| Env vars not picked up               | Check Azure App Settings or CLI-based config                             |
| GitHub Action fails                  | Confirm `AZURE_CREDENTIALS` secret is valid and Docker build succeeds    |

---

### 🛠️ Troubleshooting Notes

- **Subscription Access Issue:**  
  Initially encountered a subscription registration error:  
  `MissingSubscriptionRegistration: The subscription is not registered to use namespace 'Microsoft.Web'`.  
  This was resolved by upgrading the Azure account to a **Pay-As-You-Go** subscription.

- **Image Pull Failure:**  
  Faced an issue where the Azure App Service could not pull the Docker image.  
  Resolved after debugging deployment logs and ensuring the Docker image was built and accessible.
