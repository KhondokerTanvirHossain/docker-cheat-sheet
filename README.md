# docker-cheat-sheet

## Install Docker

1. Update server:
    ```sh
    sudo apt update
    ```

2. Install prerequisites:
    ```sh
    sudo apt-get install apt-transport-https ca-certificates curl gnupg-agent software-properties-common
    ```

3. Add Docker’s official GPG key:
    ```sh
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    ```

4. Verify the GPG key:
    ```sh
    sudo apt-key fingerprint 0EBFCD88
    ```

5. Add Docker’s official repository:
    ```sh
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    ```

6. Update server:
    ```sh
    sudo apt update
    ```

7. Install Docker:
    ```sh
    sudo apt install docker-ce docker-ce-cli containerd.io
    ```

8. Add user to the docker group:
    ```sh
    sudo usermod -aG docker $USER
    newgrp docker
    ```

9. Refresh the Bash session:
    Log out then log back in to refresh the Bash session before running any docker commands.
    ```sh
    source ~/.bashrc
    ```

10. Additional commands:
    ```sh
    sudo groupadd docker
    sudo gpasswd -a $USER docker
    sudo service docker restart
    ```

11. For CentOS installation, refer to the official documentation:
    [Docker Installation on CentOS](https://docs.docker.com/engine/install/centos/)

## Note

- Do not use only `apt` or `snap` to install Docker as it won't use the official repository.
- To get Docker information:
    ```sh
    docker info
    ```

## Install Docker via script

```bash
#!/bin/bash

# Update server
sudo apt update

# Install prerequisites
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common

# Add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

# Verify the GPG key
sudo apt-key fingerprint 0EBFCD88

# Add Docker’s official repository
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Update server
sudo apt update

# Install Docker
sudo apt install -y docker-ce docker-ce-cli containerd.io

# Add user to the docker group
sudo usermod -aG docker $USER

# Refresh the Bash session
newgrp docker

# Additional commands
sudo groupadd docker
sudo gpasswd -a $USER docker
sudo service docker restart

# Refresh the Bash session
source ~/.bashrc

# Install Docker Compose
sudo apt install -y docker-compose

echo "Docker installation completed. Please log out and log back in to refresh the Bash session."
```