# devops-manual

# Installing docker : 
```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update

sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## Prog 4: 
Showing difference between 2 different docker containers using python versions. 

### Sample Dockerfile(DockerFile311) 
```
# Dockerfile-py311 change to 2.7 not 2.07
FROM python:3.11-slim

WORKDIR /app
COPY add.py .

CMD ["python", "printer.py"]
```
> Note: Replace python version at 3.7 and not 3.07



### Sample Python script: 
```
def greet(name):
    print "Hello, " + name  # Works in Python 2.7, but not in Python 3.x

if __name__ == "__main__":
    greet("World")
```
---

### Commands to run : 

```
sudo docker build -f DockerFile307 -t lowversion .
```
> -t is the output container that we can run 

```
 sudo docker run --rm lowversion
```
> rm automatically removes the container when it exits.

If we run the above demo in two seperate python version 2.x and 3.x, the later one will throw an error without brackets.

To run a terminal in the above container : 
` docker run -it lowversion bash `

-----------------

> Side note: Pulling and using existing image on the docker repo : 
```
# Downloads and attaches to the image. 
docker run nginx
```

Prog 5 : 

Objective : Web App container run 

