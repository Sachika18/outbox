# Deployment Plan for Render (Without Dockerfiles)

## Information Gathered
- Backend: Spring Boot application using Maven, configured to use MONGODB_URI environment variable for MongoDB connection.
- Frontend: React application with standard build scripts, uses REACT_APP_API_BASE_URL and REACT_APP_WS_BASE_URL environment variables for backend communication.
- Current render.yaml uses Docker environment with Dockerfiles; needs to be updated for non-Docker deployment.
- MongoDB setup: Uses MongoDB Atlas URI, kept as is.

## Plan
- Update render.yaml to use Render's native environments (Java for backend, static-site for frontend) without Dockerfiles.
- Configure build and start commands for each service.
- Set environment variables for MongoDB URI, API base URLs, and ports.
- Deploy backend and frontend as separate services on Render.

## Dependent Files to Edit
- render.yaml: Update configuration for non-Docker deployment.

## Followup Steps
- Commit and push changes to GitHub.
- Deploy services on Render using the updated render.yaml or Render dashboard.
- Update frontend environment variables with actual backend URL after backend deployment.
- Test the deployed application.

## Steps to Complete
- [ ] Update render.yaml for backend service (Java environment).
- [ ] Update render.yaml for frontend service (static-site environment).
- [ ] Commit and push changes.
- [ ] Deploy backend service on Render.
- [ ] Deploy frontend service on Render with updated backend URL.
- [ ] Verify deployment and functionality.
