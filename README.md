# MATF-RVTECH-AWSCLOUD-2025
## How to run (LocalStack)

### Prerequisites
- Docker Desktop
- Node.js (LTS)
- npm

### Backend setup
1. Start LocalStack:
   docker compose -f dockercompose.yml up -d

2. Install dependencies:
   npm install

3. Deploy Serverless stack:
   $env:LOCALSTACK_HOSTNAME="localhost"
   npx serverless deploy --force

4. Sync Open Charge Map data:
   npx serverless invoke -f syncOCMdata --log

### Frontend setup
5. Get API Gateway endpoint:
   npx serverless info

   Copy the API ID from the `endpoint` line (between `/restapis/` and `/dev`).

6. Open `web/index.html` and paste the API ID into:
   const API_ID = 'PASTE_API_ID_HERE';

7. Deploy frontend to S3:
   npm run deploy-frontend-fixed-bucket

8. Open the S3 website URL (LocalStack) and search for a city (e.g. Belgrade).
