
### 1 - Download & Install Docker

Download docker from the [docker](https://www.docker.com/products/docker-desktop/) website and install it. Note. For windows will also need to have the [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/install) installed. 

### 2 - Download the Repository

Download the repository this tutorial is using a branch from [Clinical Trials Base Data](https://cinsw.visualstudio.com/Data%20Engineering/_git/DataEngineeringClinicalTrialsBaseData) for R and [Grants Base Data](https://cinsw.visualstudio.com/Data%20Engineering/_git/DataEngineeringGrantsBaseData?path=%2F&version=GBDocker-Testing) for Python. 

### 3 - Build the Docker Image

<aside>
💡 A Docker image is a read-only template that contains the application and its dependencies, while a container is a running instance of an image that operates in a lightweight, isolated environment. Think of a Docker image as a recipe for a dish, and a container as the actual prepared dish ready to be served and eaten. *Note. Make sure you have Docker installed before continuing.*

</aside>

Open Powershell (or terminal), and direct yourself to the directory with the Dockerfile

```powershell
cd '.\OneDrive - NSW Health Department\_FILES_DRIVE\3_repo\DataEngineeringClinicalTrialsBaseData\'
```

You can check if you are in the correct location by using the ‘ls’ command. 

![Untitled](Untitled.png)

### **Build the Image**:

Run the following command in the directory containing your Dockerfile. Replace `clinical_trials_base_data` with your desired image name. Note you can specify the version in the tag e.g. `:2.0.0`

```powershell
docker build -t clinical_trials_base_data:2.0.0 .
```

<aside>
💡 Breakdown
**`docker`**:

- This is the Docker command-line interface (CLI) command. It activates the docker engine.

**`build`**:

- This is the subcommand of `docker` that builds an image from a Dockerfile. The `docker build` command uses the Dockerfile to create a new image.

**`t`**:

- The `t` flag (short for `-tag`) allows you to specify a name and optionally a tag in the `name:tag` format for the image you are building.

`clinical_trials_base_data` is the name of the image. You can replace this with any name you prefer.

- If you want to specify a tag, you can do so by appending `:tag` to the name. For example, `clinical_trials_base_data:2.0.0`.

**`.`** :

- The dot at the end specifies the build context. The build context is the set of files that the Docker engine has access to when building the image.
- In this case, the dot represents the current directory, meaning Docker will look for the ***Dockerfile*** in the current directory and use the contents of the current directory as the context for the build (that is why we cd into it).
</aside>

You will be able to see the progress in the Powershell window. You can also check if the image has been built by using the `docker images` command in powershell/command prompt or by opening Docker Desktop and going to the **Images** section. Here you can see that we succesfully built the clinical_trials_base_data version 2.0.0 image. 

![Untitled](Untitled%201.png)

### 4 - Build the Docker Container

**Option A: Using CLI only (make sure this is in one line)**

The ‘docker run’ command creates a container with the given parameters. 

```powershell
# R
docker run -d -p 10000:8787 \
    -e USER=user \
    -e PASSWORD=password \
    -e UID_CONNECT=ci_data_assets \
    -e PWD_CONNECT=<password> \
    -v C:/Users/60260504/Documents/Repositories:/home/rstudio \
    --name dev\
    clinical_trials_base_data:2.0.0

# Python
docker run -d -p 11000:8888 \
    -e UID_CONNECT=ci_data_assets \
    -e PWD_CONNECT=<password> \
    -v C:/Users/60260504/Documents/Repositories:/home/jovyan \
    --name grants_dev\
    grants_base_data:2.0.0
  
# one line
docker run -d -p 12347:8787 -e USER=user -e PASSWORD=password -e UID_CONNECT=ci_data_assets -e PWD_CONNECT=<password> -v C:/Users/60260504/Documents/Repositories:/home/rstudio --name container_name_3 clinical_trials_base_data:2.0.0
```

**Option B: Using the Docker desktop GUI**

Using docker desktop, open the image we just created `clinical_trials_base_data:2.0.0`

![Untitled](Untitled%202.png)

Open `Optional settings` and enter the settings. Refer to the tips below.

```powershell
# Tips for building container
# Container Name (make it meaningful)
# e.g. clinical_trials_base
#-------------------------------
# Ports (Host port : Container port)
# Use host port range between 10000-20000 (rstudio typically uses 8787 as container port, python jupyter uses 8888)
# e.g. 10000
#-------------------------------
# Volumes (Host path : Container path):
# e.g. C:/Users/60260504/Documents/Repositories:/home/rstudio <- rstudio
# e.g. C:/Users/60260504/Documents/Repositories:/home/jovyan  <- python jupyter
#----------------------------------------
# Environment Variables (Variable : Value):
# e.g. for R and rstudio
# USER=user
# PASSWORD=password
# UID_CONNECT, ci_data_assets
# PWD_CONNECT, <password>
# ENV, DEV OR UAT OR PRD

```

![Untitled](Untitled%203.png)

You can see the list of containers that you have by using the `docker ps -a`  command or by examining the containers section within the Docker Desktop application. 

### 5 - Running the Container

When you go into the containers section of Docker you will see the container that was just built.

![Untitled](Untitled%204.png)

To open the rstudio container click on the port link highlighted it should look like 10000:8787. Note that the image will show the image we created before with the tag. 

![Untitled](Untitled%205.png)

You can also open the container by clicking on the name and see the logs, terminal etc. 

![Untitled](Untitled%206.png)

### R

As we set the username in the setup to user and password to password in the setup put those as the credentials

![Untitled](Untitled%207.png)

If done properly, you should see the Rstudio IDE in the browser!

![Untitled](Untitled%208.png)

Open the directory and then open the Rproj file to open the project and set it as the working directory. 

### Python

This works with a python based pipeline (e.g. Grants Base Data). You will need to build the container just like you do with R. Then copy the token for Jupyter which you can find in the Logs of the container (token = xxxx). 

![Untitled](Untitled%209.png)

And paste it in the token section and set your new password (e.g. password). Press Log in and set new password. 

![Untitled](Untitled%2010.png)

And now you are successfully in Jupyter Notebook.

![Untitled](Untitled%2011.png)

**Congratulations, you now have a working docker container!**

### 6 - Connecting / Accessing folders/volumes (e.g. SDrive/HDrive) [OPTIONAL]

If your repository requires you to access a folder or network drive such as the S drive, follow the steps below. 

**Mount the network drive**

To mount a network drive you need to create a connection to it within docker using the volume method. The example for connecting to the S drive is below. Instead of “S:/” we use the full network name that starts with ‘virtnas’. 

Make sure to update ‘username’ and ‘password’ with your stafflink username and password. This will ensure that you can access the folders you have access to in your user group. 

```powershell
docker volume create `
  --driver local `
  --opt type=cifs `
  --opt device="//virtnas-fas514.nswhealth.net/massstorage_file01/SASData/" `
  --opt o=addr=virtnas-fas514.nswhealth.net,username=60260504,password=<password>.,file_mode=0777,dir_mode=0777 `
  --name s_drive
```

Do this again to mount the H Drive 

```powershell
docker volume create `
  --driver local `
  --opt type=cifs `
  --opt device="//virtnas-fas514.nswhealth.net/share_file01/Share" `
  --opt o=addr=virtnas-fas514.nswhealth.net,username=60260504,password=<password>,file_mode=0777,dir_mode=0777 `
  --name h_drive
```

Once this is done you should see the volume in docker > volumes section

![Untitled](Untitled%2012.png)

Then you will need to mount this volume to your container in order to utilise its contents

You will need to mount the volumes through the docker command in powershell. You will need to run this code to create a container and connect to the network drive. 

```powershell
docker run -d -p 10333:8888 `
  -v s_drive:/mnt/s_drive `
  -v h_drive:/mnt/h_drive `
  -v "C:/Users/60260504/OneDrive - NSW Health Department/_FILES_DRIVE/3_repo/DataEngineeringChemotherapyBaseData:/home/jovyan" `
  -e UID_CONNECT=ci_data_assets `
  -e PWD_CONNECT=<password>`
  --name chemo_notebook_dev `
  chemo_image:2.1
  
  
  ---
  docker run -d -p 10336:8443 `
  -v s_drive:/mnt/s_drive `
  -v h_drive:/mnt/h_drive `
  -v "C:/Users/60260504/OneDrive - NSW Health Department/_FILES_DRIVE/3_repo/DataEngineeringChemotherapyBaseData:/config/workspace" `
  -e UID_CONNECT=ci_data_assets `
  -e PWD_CONNECT=viui7Io!98uPY`
  -name chemo_final `
  chemotherapy_base_data:v2.0.0
  
  [Tuesday 2:15 pm] Veronica Luu (Cancer Institute NSW)
docker run -d -p 8333:8443 `
    -v s_drive:/mnt/s_drive `
    -v h_drive:/mnt/h_drive `
    -v "C:/Users/60260504/OneDrive - NSW Health Department/_FILES_DRIVE/3_repo/DataEngineeringChemotherapyBaseData:/config/workspace" `
    -e UID_CONNECT=ci_data_assets `
    -e PWD_CONNECT=viui7Io!98uPY `
    –-name chemo_final chemotherapy_base_data:v2.0.0
 
```

You wont see the directory in the file explorer however you will still be able to access it (see below):

![Untitled](Untitled%2013.png)

**Congratulations, you are connected!**