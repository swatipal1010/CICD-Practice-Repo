## Using Jenkins server locally using Ngrok
- We'll expose the Jenkins server using ngrok
  - Ngrok can solve this problem by creating a secure tunnel between the local machine (where the Jenkins is running) and a public URL provided by Ngrok.
  - It exposes the local server to the internet, allowing GitHub servers to reach the webhook URL and send updates to Jenkins.

### Steps o install ngrok on windows
Sign-up for the Ngrok service (or any another tunneling service to your choice), then install the `ngrok` agent as [described here](https://ngrok.com/docs/getting-started/#step-2-install-the-ngrok-agent). 

Authenticate your ngrok agent. You only have to do this once:

```bash
ngrok config add-authtoken <your-authtoken>
```

Since the Jenkins service is listening on port `8080`, start ngrok by running the following command:

```bash
ngrok http 8080
```
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/f4ffc3ef-1a14-4345-9561-9e4f8a6109b1)


Your Jenkins public URL is the URL specified in the `Forwarding` line (e.g. `https://16ae-2a06-c701-4501-3a00-ecce-30e9-3e61-3069.ngrok-free.app`).
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/aaebb140-27e0-4b3b-ac11-65ae1cb70445)
- Click on visit site
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/01a0c69d-2220-48d6-aa13-06415dc664e3)

## Managing Jenkins

Most standard administrative tasks can be performed from the screens in the **Manage Jenkins** section of the dashboard.
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/06d1c9f7-518d-4ffd-87c6-d1c3b9a3ab77)


Let's take a look on some of them:

- **System**: Configure global settings and paths for the Jenkins instance. 
- **Plugins**: Add, update, remove, disable/enable plugins that extend the functionality of Jenkins. 
- **Nodes and Clouds**: Add, remove, control, and monitor the nodes used for the agents on which build jobs run.
- **Manage Credentials**: Configure the credentials that provide secure access to third-party sites and applications that interact with Jenkins.
- **Users**: Manage users defined in the Jenkins user database. This is not used if you use a different security realm such as LDAP or AD.
- **System Information**: Displays information about the Jenkins environment.
- **System Log**: Jenkins log that contains all java.util.logging output related to Jenkins.
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/286f1d43-3649-4715-89d3-ac441fb83e7f)
![image](https://github.com/swatipal1010/CICD-Practice-Repo/assets/110754474/e86d394f-e384-4914-be27-1356ff7191be)

  


