## WINDOWS

Setting up Docker on Windows involves several steps. Here’s a step-by-step guide:

### 1. **System Requirements**

Before installing Docker Desktop, make sure your Windows system meets the following requirements:

- Windows 10 64-bit: Pro, Enterprise, or Education (Build 15063 or later).
- Hyper-V and Containers Windows features must be enabled.

### 2. **Download Docker Desktop**

- Go to the [Docker Desktop for Windows download page](https://www.docker.com/products/docker-desktop).
- Download the Docker Desktop installer.

### 3. **Install Docker Desktop**

- Run the installer you downloaded.
- Follow the installation instructions:
    - During installation, the setup will ask you to authorize the installer to make changes to your system. Click "Yes".
    - The installer will also ask you to enable the Hyper-V and Containers features. Make sure these are enabled if not already.

### 4. **Start Docker Desktop**

- Once the installation is complete, Docker Desktop will start automatically.
- If not, you can start it from the Start menu.

### 5. **Enable WSL 2 Backend (Optional but Recommended)**

Docker Desktop can use Windows Subsystem for Linux 2 (WSL 2) as the backend for running Linux containers.

- **Install WSL 2**: Follow the [official Microsoft documentation](https://docs.microsoft.com/en-us/windows/wsl/install) to install WSL 2.
- **Set WSL 2 as Default**: In Docker Desktop, go to Settings -> General and check the option "Use the WSL 2 based engine".

### 6. **Configuration and Initial Setup**

- **Run Docker Commands**: Open a command prompt or PowerShell and run `docker --version` to check if Docker is installed correctly.
    
- **Pull and Run a Test Image**: Run the following command to pull and run a test image: This command will download the `hello-world` image from Docker Hub and run it in a container.
    
    ```
    docker run hello-world
    
    ```
    

### 7. **Use Docker with WSL 2**

If you have installed WSL 2, you can use Docker commands directly within your WSL 2 distributions. Open your WSL terminal and run Docker commands just as you would on Linux.

### 8. **Configure Docker Desktop Settings**

- **Preferences/Settings**: Access Docker Desktop settings by clicking on the Docker icon in the system tray and selecting "Settings".
    - **Resources**: Allocate CPU, Memory, Disk, and other resources according to your needs.
    - **Docker Engine**: Customize Docker Engine settings using the JSON configuration file.

### 9. **Install Docker Compose (Optional)**

Docker Compose is used for defining and running multi-container Docker applications.

- Docker Compose is included in Docker Desktop for Windows, so you can start using it by creating a `docker-compose.yml` file.

### 10. **Test Docker Installation**

- Run a simple Docker container to ensure everything is set up correctly:
    
    ```
    docker run -d -p 80:80 docker/getting-started
    
    ```
    

### Helpful Tips:

- **Docker CLI**: Use the Docker command-line interface (CLI) to manage your Docker containers, images, networks, and volumes.
- **Docker Hub**: Sign in to Docker Hub from Docker Desktop to access a repository of Docker images.

By following these steps, you should be able to set up Docker on your Windows machine successfully. If you run into any issues, the [Docker documentation](https://docs.docker.com/docker-for-windows/) provides comprehensive guidance and troubleshooting tips.

## MAC

Setting up Docker on a Mac is straightforward. Here’s a step-by-step guide:

### 1. **System Requirements**

Before installing Docker Desktop, ensure your macOS system meets the following requirements:

- macOS must be version 10.15 or newer.
- At least 4GB of RAM.
- VirtualBox prior to version 4.3.30 must NOT be installed (it’s incompatible with Docker Desktop).

### 2. **Download Docker Desktop**

- Go to the [Docker Desktop for Mac download page](https://www.docker.com/products/docker-desktop).
- Download the Docker Desktop installer (Docker.dmg).

### 3. **Install Docker Desktop**

- Double-click the `Docker.dmg` file you downloaded.
- Drag the Docker icon to the Applications folder.
- Open Docker from the Applications folder.

### 4. **Start Docker Desktop**

- When you start Docker for the first time, it will ask for privileged access. Enter your password to allow the necessary changes.
- Docker Desktop will start and the Docker whale icon will appear in the menu bar to indicate that Docker is running.

### 5. **Initial Setup and Configuration**

- When Docker Desktop is started, it will automatically set up Docker Engine.
    
- Open a terminal and run `docker --version` to verify the installation: This command should display the version of Docker installed.
    
    ```
    docker --version
    
    ```
    

### 6. **Test Docker Installation**

- To ensure everything is working correctly, run a simple Docker container: This command will download the `hello-world` image from Docker Hub and run it in a container. If everything is set up correctly, you will see a message indicating that the installation is successful.
    
    ```
    docker run hello-world
    
    ```
    

### 7. **Configure Docker Desktop Settings**

- Click the Docker whale icon in the menu bar and select "Preferences" to configure Docker settings.
    - **Resources**: Allocate CPU, Memory, Disk, and other resources as needed.
    - **Docker Engine**: Customize Docker Engine settings using the JSON configuration file.
    - **Advanced**: Set the Docker daemon configuration.
    - **Experimental Features**: Enable experimental features if needed.

### 8. **Install Docker Compose (Included)**

Docker Compose is included with Docker Desktop for Mac, so you can start using it immediately by creating a `docker-compose.yml` file.

### 9. **Use Docker Commands**

- Open the terminal and run Docker commands as needed. For example: This command runs a simple web server container to verify everything is working properly.
    
    ```
    docker run -d -p 80:80 docker/getting-started
    
    ```
    

### 10. **Access Docker Hub**

- Sign in to Docker Hub from Docker Desktop to access a repository of Docker images. You can do this through the Docker Desktop UI or by running:
    
    ```
    docker login
    
    ```
    

### Helpful Tips:

- **Docker CLI**: Use the Docker command-line interface (CLI) to manage your Docker containers, images, networks, and volumes.
- **Docker Hub**: Sign in to Docker Hub from Docker Desktop to access a repository of Docker images.

By following these steps, you should be able to set up Docker on your Mac successfully. For more detailed information and troubleshooting, refer to the [Docker documentation](https://docs.docker.com/docker-for-mac/).