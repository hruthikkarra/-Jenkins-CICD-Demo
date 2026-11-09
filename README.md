# Jenkins CI/CD Automation Demo

A beginner-friendly static website project for demonstrating a Jenkins pipeline.

## Project files
- `index.html` — website content
- `css/style.css` — website styling
- `Jenkinsfile` — Jenkins pipeline with Checkout, Build, Test and Deploy stages

## 1. Run locally
Open `index.html` in a web browser, or open the project folder in VS Code.

## 2. Upload to GitHub
Create a GitHub repository named `Jenkins-CICD-Demo`. In the project folder, run:

```bash
git init
git add .
git commit -m "Add Jenkins CI/CD demo project"
git branch -M main
git remote add origin YOUR_GITHUB_REPOSITORY_URL
git push -u origin main
```

Replace `YOUR_GITHUB_REPOSITORY_URL` with your repository URL.

## 3. Create the Jenkins pipeline
1. Open `http://localhost:8080`.
2. Select **New Item**.
3. Enter `Jenkins-CICD-Demo`, select **Pipeline**, and click **OK**.
4. Under **Pipeline**, set Definition to **Pipeline script from SCM**.
5. Choose **Git** and paste your GitHub repository URL.
6. Set Branch Specifier to `*/main`.
7. Set Script Path to `Jenkinsfile`.
8. Save, then click **Build Now**.

If the repository is private, configure Git credentials in Jenkins first.

## 4. Verify the result
Open the build number and select **Console Output** or **Pipeline Stage View**.
The pipeline checks out the repository, verifies the website files, runs basic content checks,
and archives the website files as a Jenkins build artifact.

## Important note
The Deploy stage in this beginner demo archives the website in Jenkins. It does not publish the
site to a public hosting service or a production server. A real deployment requires a hosting
target and deployment credentials.
