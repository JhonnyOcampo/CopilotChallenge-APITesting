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

4. We need to set up the Docker `apt` repository. Execute the following commands in the Ubuntu terminal:
    
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

7. Download the file [bankingportal-image.tar](https://drive.google.com/file/d/1H-BYg3uof64wqhVMdfoGY5figad0BIV4/view?usp=sharing) and the file [compose.yaml](compose.yaml) from this repository to your windows machine.

8. Create a folder called docker using the command `mkdir docker` in the Ubuntu terminal.
   
9. In Windows, open the File Explorer, click on the new item created called Linux and you will find a folder where you can have access to the Ubuntu files.
    
   ![image](https://github.com/user-attachments/assets/65a5875d-b81a-41db-a312-8b1ee151492a)

11. Cut and paste the downloaded files `bankingportal-image.tar` and `compose.yaml` to this path:
    ```
    \\wsl.localhost\<ubuntu>\home\<username>\docker
    ```
    `<ubuntu>` is the Ubuntu version you installted.
    `<username>` is the user name you set for Ubuntu.

12. In the Ubuntu terminal, open the folder docker `cd docker`, and execute the following commands:
    ```
    sudo docker load --input bankingportal-image.tar
    sudo docker compose up
    ```
    When the command finish loading, you can check if the API is up by opening this link in your browser `http://localhost:8180/api/dashboard/user` and verifying it returns the folllowing message:
    ![image](https://github.com/user-attachments/assets/9cfa0b85-168e-4f62-81de-9627de9bb20e)

    Now, you can start testing!

## Installing and setting up GitHub Copilot
If you have not installed or set up GitHub Copilot, please follow the instructions according to your IDE in this link [Quickstart for GitHub Copilot](https://docs.github.com/en/copilot/quickstart?tool=visualstudio)

## Where to start
1. Create a new project of your favorite programming language
2. Since GitHub Copilot needs context to generate better code suggestions, we need to provide it the following documentation:
   File | Description
   --- | ---
   [API-Documentation.md](API-Documentation.md) | This is the API documentation of the Banking Portal App, this document is more up-to-date than the one you find in the [Banking Portal wiki](https://github.com/abhi9720/BankingPortal-API/wiki), So I recommend to use this instead
   [api-docs.json](api-docs.json) | This json that contains the information of this [Swagger page](http://localhost:8180/swagger-ui/index.html)
Therefore, you need to add these files to your project and include them as context in the Copilot Chat.
4. In the Github Copilot chat, start asking questions like how to create an API test automation project or which frameworks you can use for API testing using your preferred language.
5. Then, create prompts to ask Copilot to create tests for specific features, consider the constraints that are specified in the challenge.
   
