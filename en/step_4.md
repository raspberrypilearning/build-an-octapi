## Set up the OctaPi client

One of the Raspberry Pi computers will be used as the **client machine** giving access to the servers in the OctaPi cluster. You will need to connect the usual peripherals (monitor, keyboard, mouse) to this Raspberry Pi in order to use it to control the OctaPi.

- On your micro SD card, install the latest version of Raspbian by following the [software guide instructions](https://www.raspberrypi.org/learning/software-guide/quickstart/){:target="_blank"}.

- Using this micro SD card, boot up the Raspberry Pi 3 with a keyboard, screen, and mouse connected.

- Ensure the Raspberry Pi is also connected to the internet.

- Open a terminal window.

    ![Open a terminal](images/terminal.png)

- Install `dispy` by typing this command into the terminal:

    ```bash
    sudo pip3 install dispy==4.7.1
    ```

    Dispy is a distributed Python implementation that will allow you to write code on the client and run it across the servers. **Note**: It is crucial that you install version 4.7.1 of `dispy`, as later versions rely on a library that is currently incompatible with Raspbian.

    Further information is available from [dispy: Distributed and Parallel Computing with/for Python](http://dispy.sourceforge.net/index.html){:target="_blank"}.

- Install `nmap` by typing this command into the terminal:

    ```bash
    sudo apt-get install nmap
    ```

    Nmap is used to discover the IP addresses of the Raspberry Pi servers forming the OctaPi cluster, so that they can be shut down or rebooted as needed.

- If you are using the optional Unicorn HATs, install the software for them by typing this command into the terminal:

    ```bash
    curl https://get.pimoroni.com/unicornhat | bash
    ```

    You will need to reboot your Pi after installing this.

- Make sure you are in the `/home/pi` directory, then download the OctaPi client software by typing this command into the terminal:

    ```bash
    git clone https://github.com/raspberrypilearning/octapi-setup.git
    ```
    The client software contains source code examples in Python 3 and a bash control script for rebooting and shutting down the cluster. The control script can be used with the Unicorn HAT as well.

- Move all of the files from the `client` folder you just downloaded into the `/home/pi` folder:

    ```bash
    mv /home/pi/octapi-setup/client/* /home/pi
    ```

- Shut down your new OctaPi client for the time being and set aside the client SD card in a safe place.
