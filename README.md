# google-cloud-run-job-template-go
Basic template for google cloud jobs written in Go.  

Focused on deploying and updating your jobs from the local environment.

# Prerequisites  
- GCP Project with billing and relevant APIs enabled
- Gcloud CLI configured and logged in

# Inital deployment 
1. Create the Artifact Registry repository  
```
glcoud artifact repositories create REPOSITORY_NAME --repository-format=docker \
--location=REPOSITORY_REGION
```

2. Define the Image Url 
```
image_url=REPOSITORY_REGION-docker.pkg.dev/PROJECT_ID/REPOSITORY_NAME/IMAGE_NAME:IMAGE_TAG
```

2. Build the app with Cloud Build  
```
gcloud builds submit \
--region=REPOSITORY_REGION \
--tag $image_url 
```

3. Deploy the job with on Cloud Run
```
gcloud run jobs deploy JOB_NAME --region=JOB_REGION --
