## Creating a pipeline in Jenkins using Jenkinsfile
### Writing a build.Jenkinsfile in the root directory of the roberta application
```text
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'ls'
                sh 'echo building...'
            }
        }
    }
}
```

The Jenkinsfile you've provided is written in Declarative Pipeline syntax.
Commit and push the changes to your repository

### Defining the pipeline in the Jenkins
From the main Jenkins dashboard page, choose **New Item**.
 ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/0cf2da0f-9d33-4d6e-91f1-695d798de7ea)
 
1. Enter the project name (e.g. `RobertaBuild`), and choose **Pipeline**.
  ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/a6f52ac5-987d-46c2-bf1f-ba3643fad472)

3. Check **GitHub project** and enter the URL of your GitHub repo.
4. Under **Build Triggers** check **GitHub hook trigger for GITScm polling**.
5. Under **Pipeline** choose **Pipeline script from SCM**.
6. Choose **Git** as your SCM, and enter the repo URL.
7. If you don't have yet credentials to GitHub, choose **Add** and create **Jenkins** credentials.
   1. **Kind** must be **Username and password**
   2. Choose informative **Username** (as **github** or something similar)
   3. The **Password** should be a GitHub Personal Access Token with the following scope:
      ```text
      repo,read:user,user:email,write:repo_hook
      ```
      Click [here](https://github.com/settings/tokens/new?scopes=repo,read:user,user:email,write:repo_hook) to create a token with this scope.
   4. Enter `github` as the credentials **ID**.
   5. Click **Add**.
8. Under **Branches to build** enter `main` as we want this pipeline to be triggered upon changes in branch main.
9. Under **Script Path** write the path to your `build.Jenkinsfile` defining this pipeline.
10. **Save** the pipeline.
11. Test the integration by add a [`sh` step](https://www.jenkins.io/doc/pipeline/tour/running-multiple-steps/#linux-bsd-and-mac-os) to the `build.Jenkinsfile`, commit & push and see the triggered job.
