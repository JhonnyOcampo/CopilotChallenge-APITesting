# GitHub Copilot Challenge for API Testing

In order to practice what we have learned so far, we will be working on a testing challenge. The challenge consists of creating an automation test suite for an API of a [Banking Portal.](https://github.com/abhi9720/BankingPortal-API)

## Challenge
From scratch, create a test automation project in any programming language and framework of your choice, but it should fulfill the following requirements:
1. The project should be implemented using GitHub Copilot.
2. The tests should be written using Gerkin syntax, it means the project should implement a BDD framework.
3. The project should implement a dependency management tool (e.g. Maven).
4. The project should generate a report after running the tests.
5. Create a Pipeline that runs all the tests and generates a report, you can use any CI/CD tool of your choice and with the help of Copilot write the infraestructure code needed.
6. Create test cases for at least the following features:
    - Register user
    - Login user
    - Create a PIN
    - Deposit funds

## Setting up the API to be tested
In order to run the application that exposes the API, we need to install and configure WSL2 and Docker Compose.

1. From the company portal app, look for WSL2 and click on install.
   ![image](https://github.com/user-attachments/assets/d7602fae-6acf-4fee-a66d-d86b0d4c12d9)

2. From the Microsoft Store app, search for Ubuntu and install the latest version of Ubuntu.
   ![Captura de pantalla 2025-02-04 161620](https://github.com/user-attachments/assets/14bddde0-ada4-4dbc-99c3-9d962e9e9051)

3. After installing Ubuntu, click open and a Windows terminal will ask you to create a username and password for Ubuntu.
   ![Captura de pantalla 2025-02-04 162921](https://github.com/user-attachments/assets/08171a3f-11cf-4fe7-8bfa-5310ce6990df)

   You can also access Ubuntu if you manually open a windows terminal (Command Prompt app), select the down arrowhead located at the top and then click on Ubuntu:
   
   ![Captura de pantalla 2025-02-05 000832](https://github.com/user-attachments/assets/9d6010a9-4bfb-46d3-90ee-ffab703c798f)

5. We need to set up the Docker `apt` repository. Execute the following commands in the Ubuntu terminal:

```
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

5. Install the Docker packages:

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

6. Verify that the installation is successful by running the `hello-world` image:
```
sudo docker run hello-world
```
This command downloads a test image and runs it in a container. When the container runs, it prints a confirmation message and exits.


