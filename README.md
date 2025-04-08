# Deploy a Python Application using Jenkins CI/CD Pipeline

1. Launch an EC2 Instance in AWS cloud platform
2. Connect to the EC2 Instance
3. Update the packages
4. Install Docker, Jenkins and Git
5. Create a directory and configure Git, then initialize .git repository in that directory.
6. Create a sample python app, then add, commit and push the app to remote repository.
7. Create a Dockerfile, then add, commit and push the Dockerfile to remote repository.
8. Build the docker image manually to check whether Dockerfile is working properly or not.
9. If image got created then launch a container using that image.
10. Now configure the Jenkins dashboard.
11. Create a pipeline job using Jenkinsfile(which will be fetched from GitHub repository).
12. Add Docker credentials in Jenkins global credentials store.
13. Add GitHub webhook to trigger the pipeline automatically after every push to main branch.
14. Create a Jenkinsfile, then add, commit and push the Jenkinsfile to remote repository.
15. After push the Pipeline will be automatically triggered.
16. After successful build check in your terminal if docker image and container got created or not.
17. Browse your base machine on port 5000 to see the Container's output.
