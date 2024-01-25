# ODOO + Github Action

Execute CICD workflow for private Odoo repo

## Setup

1. **Build image**

   - Follow instructions in the file [.build/README.md](.build/README.md)

1. **Setup CI/CD**

   - \# TODO: Update description of CI/CD here

   - Sometimes we cannot authenticate by SSH

     ```plaintext
     <https://github.com/garygrossgarten/github-action-ssh/issues/20>
       at SSH2Stream.Writable.write (node:internal/streams/writable:336:10) {
     level: 'client-authentication'
     ```

   - **Solution:**

     ```bash
     # Generate SSH key using a different algorithm
     ssh-keygen -t ecdsa -b 521
     ```

1. **Deploy**

   - Follow instructions in the file [.deploy/README.md](.deploy/README.md)

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

-
