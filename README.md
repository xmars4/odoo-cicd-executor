# ODOO + Github Action

## Execute CICD workflow for private Odoo repo

### Setup

For a newly Odoo repository that needs a CICD process, follow the instructions below:

1. Determine repo name *(1)*, e.g., vdx-vn/cuu-long.
1. Checkout a new branch name *(1)* from the production branch.
1. Replace `<private_repo_path>` value in the file [private-cicd.yml](.github/workflows/private-cicd.yml) with *(1)*.
1. Go to [repo settings](https://github.com/xmars4/odoo-cicd-executor/settings/secrets/actions) and create a new environment named *(1)* with the following secrets and variables:

   - *Environment secrets:*
     - **ACCESS_TOKEN**: PAT for access to the private repo
     - **SERVER_DB_PASSWORD**: Server database password for the backup process
     - **SERVER_PRIVATE_KEY**: Server private key file for access to the server through SSH or SCP protocol
     - **TELEGRAM_CHANNEL_ID**: Telegram channel ID for notifications through the Telegram channel
     - **TELEGRAM_TOKEN**: Telegram BOT token (the BOT added to this TELEGRAM_CHANNEL_ID)

   - *Environment variables:*
     - **BRANCH**: Branch name of the private repo that needs CICD process
     - **DB_IMAGE_TAG**: Postgres image tag name defined in the docker-compose.yml file of the private repo
     - **ODOO_IMAGE_TAG**: Odoo image tag name defined in the docker-compose.yml file of the private repo
     - **PATH**: Private repo GitHub path
     - **SERVER_DEPLOY_PATH**: Server deployment path, the folder containing the docker-compose.yml file
     - **SERVER_HOST**: Server IP address
     - **SERVER_ODOO_DB_NAME**: Odoo database name
     - **SERVER_ODOO_URL**: Odoo URL
     - **SERVER_PORT**: Server SSH port
     - **SERVER_USER**: Username for SSH connection

1. Use [this template repository](https://github.com/xmars4/odoo-cicd-github-action) to create a new repo named *(1)*.
1. Check the file *.github/workflows/cicd.yml* on the new repo and edit accordingly to your contribution workflow:

   - Pull request
   - Direct commit

1. Start coding

### Problems & Solutions

1. **Non-expired PAT (personal access token) when checking out another repo**

   ![img/erro_non_expired_token.png](img/erro_non_expired_token.png)

   - **Solution:** Set an expiration date for the PAT

2. **Cannot authenticate by SSH**

   ![img/erro_ssh_action.png](img/erro_ssh_action.png)

   - **Solution**:

     ```bash
     # Generate SSH key using a different algorithm
     ssh-keygen -t ecdsa -b 521
     ```
