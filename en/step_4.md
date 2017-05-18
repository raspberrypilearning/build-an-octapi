# Set up the OctaPi client

One of the Raspberry Pi computers will be used as the **client machine** giving access to the servers in the OctaPi cluster. You will need the usual peripherals (monitor, keyboard, mouse) connected to this Raspberry Pi in order to use it to control the OctaPi.

1. On your SD card, install the latest version of Raspbian by following the [software guide instructions](https://www.raspberrypi.org/learning/software-guide/quickstart/)

1. Boot up the Raspberry Pi 3 using this micro SD card with a keyboard, screen and mouse connected and ensure you are connected to the internet.

1. Open a terminal window

    ![Open a terminal](images/terminal.png)

1. Install the **dispy** software by typing this command into the terminal:

    ```bash
    sudo pip3 install dispy
    ```

    Dispy is a distributed Python implementation that will allow you to write code on the client and run it across the servers.

    Further information on Dispy is available from [dispy: Distributed and Parallel Computing with/for Python](http://dispy.sourceforge.net/index.html)

1. Install the **nmap** software by typing this command into the terminal:

    ```bash
    sudo pip3 install nmap
    ```

    Nmap is used to discover the IP addresses of the Raspberry Pi servers forming the OctaPi cluster, so that they can be shut down or rebooted as needed.

1. If you are using the optional Pimoroni **Unicorn HATs**, install the software for them by typing this command into the terminal:

    ```bash
    curl https://get.pimoroni.com/unicornhat | bash
    ```


1. Download the OctaPi client software by typing this command into the terminal: **[TO DO: ADD THIS URL ONCE KNOWN]**

    The client software contains source code examples in Python 3 and a control bash script for rebooting and shutting down the cluster
    Download the `start_unicorn.sh` bash script for installation on the server

    ```bash
    wget url.to.be.decided
    ```

    If you are using the optional Unicorn HATs the control script can be used with them too.


1. Shutdown your new OctaPi client for the time being and set aside the client SD card in a safe place.
