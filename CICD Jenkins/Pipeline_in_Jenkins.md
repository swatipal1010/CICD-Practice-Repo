## Creating a pipeline in Jenkins using Jenkinsfile
### Writing a build.Jenkinsfile in the root directory of the roberta application
```text
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'ls'                  //bat 'dir' for Windows
                sh 'echo building...'   //bat 'echo building...' for Windows
            }
        }
    }
}
```

The Jenkinsfile you've provided is written in Declarative Pipeline syntax.
Commit and push the changes to your repository

### Defining the pipeline in the Jenkins
1. From the main Jenkins dashboard page, choose **New Item**.
   
 ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/0cf2da0f-9d33-4d6e-91f1-695d798de7ea)
 
2. Enter the project name (e.g. `RobertaBuild`), and choose **Pipeline**.
  ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/a6f52ac5-987d-46c2-bf1f-ba3643fad472)

3. Check **GitHub project** and enter the URL of your GitHub repo.
   ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/e720e65d-998e-440c-baac-04009184a9a0)

4. Under **Build Triggers** check **GitHub hook trigger for GITScm polling**.
   ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/86452d73-f7b5-4e31-8861-a402e6030534)

5. Under **Pipeline** choose **Pipeline script from SCM**.
   ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/96333257-28bc-456b-9a8c-edbedbf29272)

6. Choose **Git** as your SCM, and enter the repo URL.
    ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/0a1681b9-c105-4c6b-8df4-b0d561bb24c9)

7. If you don't have yet credentials to GitHub, choose **Add** and create **Jenkins** credentials.
    ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/fcfb069a-cb76-465a-b74d-480fbe1ac9f7)

   1. **Kind** must be **Username and password**
   2. Choose informative **Username** (as **github** or something similar)
      ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/5634fa22-812f-4881-abc4-836f880e8bad)

   3. The **Password** should be a GitHub Personal Access Token with the following scope:
      ```text
      repo,read:user,user:email,write:repo_hook
      ```
      Click [here](https://github.com/settings/tokens/new?scopes=repo,read:user,user:email,write:repo_hook) to create a token with this scope.
   4. Enter `github` as the credentials **ID**.
      ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/61618f56-a5af-4eec-b3be-bf15ed0653ba)

   5. Click **Add**.
8. Under **Branches to build** enter `main` as we want this pipeline to be triggered upon changes in branch main.
    ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/071afe7e-66da-44de-aadb-fded9b40221c)

9. Under **Script Path** write the path to your `build.Jenkinsfile` defining this pipeline.
    ![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/397a0dbc-818c-4a13-89da-643b2c5a1a77)

10. **Save** the pipeline.
11. Test the integration by add a [`sh` step](https://www.jenkins.io/doc/pipeline/tour/running-multiple-steps/#linux-bsd-and-mac-os) to the `build.Jenkinsfile`, commit & push and see the triggered job.
