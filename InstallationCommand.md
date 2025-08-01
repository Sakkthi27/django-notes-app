1  sudo apt update && sudo apt upgrade -y
    2  sudo apt install openjdk-11-jdk
    3  wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add - 
    4  sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    5  wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add - 
    6  sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
    7  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA
    8  sudo apt install jenkins
    9  clear
   10  sudo apt update
   11  sudo apt install fontconfig openjdk-17-jre
   12  java --version
   13  sudo wget -O /usr/share/keyrings/jenkins-keyring.asc   https://pkg.jenkins.io/debian/jenkins.io-2023.key
   14  echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]"   https://pkg.jenkins.io/debian binary/ | sudo tee   /etc/apt/sources.list.d/jenkins.list > /dev/null
   15  sudo apt-get update
   16  sudo apt-get install jenkins
   17  sudo systemctl status jenkins
   18  cd /var/lib/jenkins/secrets/initialAdminPassword
   19  sudo cat  /var/lib/jenkins/secrets/initialAdminPassword
   20  sudo apt-get update
   21  sudo apt-get install     ca-certificates     curl     gnupg     lsb-release
   22  sudo mkdir -p /etc/apt/keyrings
   23  curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
   24  echo   "deb [arch=$(dpkg --print-architecture) \
   25    signed-by=/etc/apt/keyrings/docker.gpg] \
   26    https://download.docker.com/linux/ubuntu \
   27    $(lsb_release -cs) stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   28  sudo apt-get update
   29  sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
   30  docker --version
   31  sudo usermod -aG docker jenkins
   32  sudo systemctl restart jenkins
   33  sudo apt-get install wget apt-transport-https gnupg lsb-release
   34  wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
   35  echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
   36  sudo apt-get update
   37  sudo apt-get install trivy
   38  df -h
   39  # Remove stopped containers
   40  docker container prune -f
   41  # Remove unused images
   42  docker image prune -a -f
   43  # Remove unused volumes
   44  docker volume prune -f
   45  # Remove unused networks
   46  docker network prune -f
   47  sudo su
   48  lsblk
   49  df -h
   50  docker login
   51  docker login -u devski
   52  ls
   53  docker ls
   54  docker ps
   55  sudo su
   56  docker ps
   57  sudo su
   58  sudo docker ps
   59  sudo usermod -aG docker jenkins
   60  sudo systemctl restart jenkins
   61  docker ps -a
   62  sudo docker ps -a
   63  docker run -d -p 8000:8000 --name test-notes-container devski/my-notes-app:latest
   64  sudo su
   65  sudo curl -L "https://github.com/docker/compose/releases/latest/download/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
   66  sudo chmod +x /usr/local/bin/docker-compose
   67  docker-compose
   68  docker-compose ps
   69  docker compose ps
   70  sudo cat /var/lib/jenkins/secrets/initialAdminPassword
   71  history
   72  curl http://localhost:8000
