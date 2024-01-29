# ODOO + Github Action

Execute CICD workflow for private Odoo repo

## Setup

For a newly Odoo repository, that need CICD process, following below instructions:

1. Determine repo name *(1)*
e.g: vdx-vn/cuu-long

1. Create new branch  name *(1)* from production branch

1. Replace <private_repo_path> value in file [private-cicd.yml](.github/workflows/private-cicd.yml) by *(1)*

1. Go to [repo setting](https://github.com/xmars4/odoo-cicd-executor/settings/secrets/actions), create new environment named *(1)*
with following secrets and variables:\

    - *Environment secrets:*

- **ACCESS_TOKEN**: PAT for access to private repo
- **SERVER_DB_PASSWORD**: Server database password, for backup process
- **SERVER_PRIVATE_KEY**: Server private key file, for access to server through ssh or scp protocol
- **TELEGRAM_CHANNEL_ID**: Telegram channel ID, use for notification through Telegram channel
- **TELEGRAM_TOKEN**: Telegram BOT token, the BOT added to  this TELEGRAM_CHANNEL_ID

    - *Environment variables:*

- **BRANCH**: Branch name of private repo that need need cicd process
- **DB_IMAGE_TAG**: Postgres image tag name, defined in docker-compose.yml file of private repo
- **ODOO_IMAGE_TAG**: Odoo image tag name, defined in docker-compose.yml file of private repo
- **PATH**: Private repo GitHub path
- **SERVER_DEPLOY_PATH**: Server deployment path, the folder contains docker-compose.yml file
- **SERVER_HOST**: Server IP address
- **SERVER_ODOO_DB_NAME**: Odoo database name
- **SERVER_ODOO_URL**: Odoo url
- **SERVER_PORT**: Server SSH port
- **SERVER_USER**: Username for SSH connection

1. Use [this template repository](https://github.com/xmars4/odoo-cicd-github-action) to create a new repo name *(1)*

1. Check file *.github/workflows/cicd.yml* on the new repo, edit accordingly to your contribution workflow

- Pull request
- Direct commit

## Problems & Solutions

1. **Non-expired PAT (personal access token) when checking out other repo**

    ![img/erro_non_expired_token.png](img/erro_non_expired_token.png)

- **Solution:** Set an expiration date for the PAT

1. **Cannot authenticate by SSH**

   ![img/erro_ssh_action.png](img/erro_ssh_action.png)

- **Solution**:

    ```bash
     # Generate SSH key using a different algorithm
     ssh-keygen -t ecdsa -b 521
     ```
