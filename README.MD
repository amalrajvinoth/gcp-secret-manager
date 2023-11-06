## Retrieving Credentials/Secrets from GCP Secret Manager with Spring Boot

Store a secret in Secret Manager, then build simple Spring Boot microservices and retrieve the secret.

https://codelabs.developers.google.com/codelabs/cloud-spring-cloud-gcp-secret-manager#0


### Setup
- [Create GCP project](https://codelabs.developers.google.com/codelabs/cloud-spring-cloud-gcp-secret-manager#1)
- Create service account
- Impersonate service account
```shell
gcloud auth application-default login --impersonate-service-account <SERVICE_ACC_EMAIL>.iam.gserviceaccount.com
```
- Set environment variable GOOGLE_APPLICATION_CREDENTIALS
```shell
export GOOGLE_APPLICATION_CREDENTIALS="$HOME/.config/gcloud/application_default_credentials.json"
```
- Enable service & add access policy
```shell
gcloud projects add-iam-policy-binding <PROJECT_ID> --member="serviceAccount:<SERVICE_ACC>@<PROJECT_ID>.iam.gserviceaccount.com" --role=--role=roles/iam.serviceAccountTokenCreator

gcloud services enable secretmanager.googleapis.com
```
- Check iam policies for the project
```shell
gcloud projects get-iam-policy <PROJECT_ID>
```

### Troubleshooting
- When you see `Gaia id not found` which means you are not configured the service account properly.

### Reference
- https://cloud.google.com/docs/authentication/use-service-account-impersonation
- https://cloud.google.com/docs/authentication/provide-credentials-adc#how-to
- https://spring-gcp.saturnism.me/app-dev/cloud-services/secret-management
- https://codelabs.developers.google.com/codelabs/cloud-spring-cloud-gcp-secret-manager#0
