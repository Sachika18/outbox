# Deployment Instructions for Render

To deploy your backend and frontend separately on Render without Dockerfiles, follow these steps:

## Prerequisites
- Your project repository contains the updated `render.yaml` file with the correct configuration.
- You have a Render account and are logged in at https://render.com.
- Your project repository is connected to Render via GitHub.

## Backend Deployment

1. Go to Render dashboard and click **New** > **Web Service**.
2. Select your GitHub repository.
3. Name the service `backend`.
4. Choose the branch to deploy.
5. Set the environment to **Docker** (since Java environment is not available).
6. Set the build command to:
   ```
   ./mvnw clean package -DskipTests
   ```
7. Set the start command to:
   ```
   java -jar target/Backend-0.0.1-SNAPSHOT.jar
   ```
8. Add environment variables:
   - `PORT` = `8080`
   - `MONGODB_URI` = your MongoDB connection string (same as in your local setup)
9. Choose the free plan or your preferred plan.
10. Enable **Auto-Deploy** if you want automatic redeploys on push.
11. Click **Create Web Service**.

## Frontend Deployment

1. Go to Render dashboard and click **New** > **Static Site**.
2. Select your GitHub repository.
3. Name the service `frontend`.
4. Choose the branch to deploy.
5. Set the build command to:
   ```
   npm install && npm run build
   ```
6. Set the publish directory to:
   ```
   build
   ```
7. Add environment variables:
   - `REACT_APP_API_BASE_URL` = `https://<your-backend-service>.onrender.com/api`
   - `REACT_APP_WS_BASE_URL` = `https://<your-backend-service>.onrender.com`
8. Choose the free plan or your preferred plan.
9. Enable **Auto-Deploy** if you want automatic redeploys on push.
10. Click **Create Static Site**.

## Post Deployment

- After deployment, update the frontend environment variables with the actual backend URL provided by Render.
- Test the frontend URL to ensure it communicates correctly with the backend.
- Monitor logs and troubleshoot any issues via the Render dashboard.

This process will deploy your backend and frontend separately on Render using Docker for backend and static site for frontend, while keeping your current MongoDB setup intact.
