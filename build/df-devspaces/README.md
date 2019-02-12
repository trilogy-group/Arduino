# Arduino Development with DevSpaces 

## DF DevSpaces CLI Installation

You can download the setup file in [this link](https://www.devspaces.io/devspaces/download) and follow the install steps [here](https://support.devspaces.io/article/22-devspaces-client-installation).

* To download the DevSpaces CLI, you need to login using your GitHub account.

* After installation, you can use DevSpaces CLI by running `devspaces` command in the command line. It will show all actions that you can do with DevSpaces.


## Create a new DevSpace from a public Docker Image

There is a public Docker image with all the dependencies needed to build the Arduino project (`devspaces/arduino`). So, to create a DevSpace based on this image, please, follow the steps below:

1. Go to the [DevSpaces Web UI](https://devspaces.io/devspaces/landing) and click on **Create from a public Docker Image** option.

1. Write `arduino` inside the search field and click on the **Select Repository** button next to the repository with the name `Arduino` and owner `arduino`.

1. Choose a name or leave the suggested name and click **Next**.

1. Write `devspaces/arduino` inside the Dockerhub Image Name field and select the repository with this name on the drop-down list. Then, click on **Pull docker image**. It will pull the image and make it available to be used by DevSpaces.

1. Once the image is pulled, a **Next** button will appear. You can click on it.

1. Just skip the ports configuration clicking on **Next** again. After that, you can configure the environment variables or leave as is. Then, click **Next**.

1. It will show an overview of the DevSpace. If everything is ok you can click on **Validate Container**. It will start the validation process that takes at least 2 minutes to be done.

1. When the validation process is over, you can start the container by clicking on the **Start DevSpace** button. Then, go to the DevSpaces list, to see the DevSpace status, by clicking on **Go to My DevSpaces**.

1. With the `Running` status, you can open a terminal to the created DevSpaces. To do that just open a local terminal and run the following command:

        devspaces exec Arduino

1. Inside the oppened terminal you can clone (or bind the local repository), do the changes that you need on the code, and build it.

* **Important Note:** Arduino is a Desktop application that uses the GUI of the operational system. DF DevSpaces doesn't support the usage of X11 Server. So, it is not possible to run the built project inside the container. However, after the build, it is showed a message with the path to the installer. You can run in the local environment, if you want.

## Binding the local repository on DevSpace

To bind a folder to the created and started DevSpace, it is needed to follow the steps below:

* Make sure that the DevSpace is `Running` using the `devspaces ls` command.
* With a running DevSpace, move to the root folder of the repository in the local machine.
* Run the below command to bind the current folder:

        devspaces bind firm58-dev

* Wait to get all files synced. To see if the sync is finished, open a browser and access http://localhost:49152/. You will see a page like the one below. If the sync is finished, you will see the **Up to date** green message next to the **Remote Device** block.
* When you get the sync up to date, everything that is changed, deleted or created inside the local folder or in the `/data` folder inside the container will be synced. The sync is bidirectional. 
* **Note:** If you want to stop the bind, just run the command:

        devspaces unbind scalearc
