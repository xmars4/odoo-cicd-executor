# ODOO + Github Action

Execute CICD workflow for private Odoo repo

## Setup

For a newly Odoo repository, we create a new environment in this repo.
Follow followi

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

.
