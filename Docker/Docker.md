## Docker

### Download Docker engine(Linux)

1. Allow apt over https

```
sudo apt-get update
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

2. Add Docker GPG key

```
sudo mkdir -m 0755 -p /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

3. Setup the repo

```
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

4. Update apt index

```
sudo apt update
```

5. Install latest Docker Engine, containerd, and Docker Compose.

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

6. Non root access

```
sudo usermod -aG docker $USER
```

Reboot the system and it's done!

## Docker Commands

- Run Container: `Docker run [options] <image>`

- Pull Image: `docker pull [options] <image>`

- Stop Container: `docker stop <containerId>`

- Start Container: `docker start <containerID>`

- Delete Container: `docker rm <containerID>`

- Copy files into container: `docker cp ./path  <containerId>:./path`
  > Note: invert arguments to copy from container to host

- Expose container: `Docker run -p <externalPort>:<internalPort> [options] <image>`


## Docker Registry Commands

- Create Image: `docker commit -p <containerId> <name>:<label>`

- Push Image

