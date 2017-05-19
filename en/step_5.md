# Set up one OctaPi server

Each of the Raspberry Pi 3 computers which will form the OctaPi cluster needs to have its own micro SD card prepared. However, as each card is identical, you can set up just one server and check it's working before replicating the SD card for the other servers.

1. On a fresh SD card, install the latest version of Raspbian by following the [software guide instructions](https://www.raspberrypi.org/learning/software-guide/quickstart/)

1. Boot up a Raspberry Pi 3 using this SD card with a keyboard, screen and mouse connected. Also ensure you are connected to the internet before proceeding.

1. Open a terminal

    ![Open a terminal](images/terminal.png)

1. As with the client, install the **dispy** software by typing this command into the terminal:

    ```
    sudo pip3 install dispy
    ```

1. Install the **psutils** software by typing this command into the terminal:

    ```
    sudo pip3 install psutils
    ```

    This software is used by **dispy** for reporting CPU usage by the servers in the cluster.


1. If you are using the optional Pimoroni **Unicorn HATs**, install the software for them by typing this command into the terminal:

    ```
    curl https://get.pimoroni.com/unicornhat | bash
    ```

    Make sure you are in the `/home/pi` folder and also download the `start_unicorn.sh` bash script for installation on the server

    ```bash
    wget https://raw.githubusercontent.com/raspberrypilearning/octapi-setup/server/start_unicorn.sh
    ```

1. Go back to the terminal window and type the following command to begin editing the `\etc\rc.local` file:

    ```
    sudo nano \etc\rc.local
    ```

1. At the bottom of the file add the following lines to run the **dispy** server software as a daemon each time the server boots:

    ```bash
    sleep 20
    _IP=$(hostname -I);
    dispynode.py -i "$_IP" --client_shutdown --daemon
    ```

    **Note:** The sleep for 20 seconds is to allow time for the server to log onto your Wi-Fi router and obtain a network IP address from it. We need the IP address so that the server will listen for the client on the network properly. You may need to adjust the amount of delay to suit the router you are using.

1. Press `Ctrl` + `o` to save your changes, then `Ctrl` + `x` to exit the nano editor.

1. Check that remote login via SSH is enabled so that remote command line access to your server is possible. Under the Preferences menu, select Raspberry Pi Configuration
    ![Enable SSH](images/enable-ssh1.png)

    Then click on the **Interfaces** tab and make sure that SSH is enabled.

    ![Enable SSH](images/enable-ssh.png)
