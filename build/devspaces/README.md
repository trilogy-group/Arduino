# Arduino Development with DevSpaces 

## DF DevSpaces CLI Installation

You can download the setup file in [this link](https://www.devspaces.io/devspaces/download) and follow the install steps [here](https://support.devspaces.io/article/22-devspaces-client-installation).

* To download the DevSpaces CLI, you need to log in using your GitHub account.

## DF DevSpaces CLI Usage

After installation, you can use DevSpaces CLI by running `devspaces` command in the command line. It will show all actions that you can do with DevSpaces.

### Start a new DevSpace for Arduino

Please, follow these steps to create a new DevSpace and build the Arduino project inside it:

1. Move to `build/devspaces` folder. This folder contains all resources that are needed to create the DevSpace.

        cd build/devspaces

1. Create the DevSpace by running the following command. A new window will be shown with the build status.

        devspaces create
    
    * The notification system will shown a message when the build is finished. Then the validation process starts (it takes at least 2 minutes).

1. When the validation process is finished, you can start the the DevSpace by running the following command. 

        devspaces start Arduino

    * The notification system will inform when the start is finished.

1. You can enter the created DevSpace by running the following command. 

        devspaces exec Arduino

### Bind the Repository Folder to the DevSpace

To bind a folder to the created and started DevSpace, it is needed to follow the steps below:

1. Make sure that the DevSpace is `Running` using the `devspaces ls` command.

1. With a running DevSpace, move to the folder that you clonned the repository locally. If you are in the `build/devspaces`, just go back to the root folder:

        cd ../..

1. Run the following command to bind the current folder:

        devspaces bind Arduino

1. Wait to get all files synced. To see if the sync is finished, open a browser and access http://localhost:49152/. You will see a page like the one below. If the sync is finished, you will see the **Up to date** green message next to the **Remote Device** block (see the [demo](https://jira.devfactory.com/secure/attachment/624734/Arduino%20Import.mp4) to get details about that).

   * Now, everything that is changed or created inside the local folder or in the `/data` folder inside the container will be synced. The sync is bidirectional. 

   * If you want to stop the bind, just move to the bonded folder and run the command:

                devspaces unbind Arduino

### Build and Run Arduino

1. To run a build inside the DevSpaces, just run the following command inside the `build` folder:

        ant dist

* **Important Note:** Arduino is a Desktop application that uses the GUI of the operational system. DF DevSpaces doesn't support the usage of X11 Server. So, it is not possible to run the built project inside the container. However, after the build, it shows a message with the path to the installer. You can run in the local environment, if you want, by following the steps below (see the [demo](https://jira.devfactory.com/secure/attachment/624734/Arduino%20Import.mp4) to get details about that):

    1. Extract the `tar.xz` generated after the build:

                tar -xvf linux/arduino-1.8.9-linux64.tar.xz

    1. Then, go to the extracted folder and run arduino executable:

                cd arduino-1.8.9
                ./arduino

    * **Note:** Depending on the X11 Server configuration that you are using, maybe the command above throws an error saying `No X11 display variable was set`. To fix it you need to set an environment variable `DISPLAY` as follows. It will configure the current terminal to use the first display (default) that exists on the machine.

                export DISPLAY=:0

