## Set up the client on the OctaPi network

- Connect a monitor, keyboard, and mouse and power up a Raspberry Pi containing the **client** SD card you created earlier.

- Repeat the instructions from the previous step on this computer, logging into the 'OctaPi' network and removing any alternative WiFi details from `wpa_supplicant` file.

- Keeping the client switched on, boot up a single **server** Raspberry Pi with only a power lead connected.

- Open a terminal window on the **client** Raspberry Pi.

- Type the following command to find the IP address of the **client** Raspberry Pi:

    ```bash
    hostname -I
    ```

- Type the following command to find out the IP address of the **server** Raspberry Pi:

    ```bash
    nmap -sP 192.168.1.*
    ```

    Make a note of the **server** IP address (you should see the router's address, which will be `192.168.1.1`, and the client's address listed, too).

    **Note:** The `nmap` software scans the network to find the IP addresses of the devices connected to it. We need to do this on our local network so that the client machine can communicate with the Raspberry Pi computers which form the OctaPi cluster. **Do not run nmap on a network that is connected to the internet.** `nmap` is a powerful piece of software and using it to scan a network you do not own may be considered hacking, and in some countries may even be illegal.

- On the **client**, run `ssh-keygen` in the terminal to create a key for authenticating the client with the server.

    ```bash
    ssh-keygen
    ```

    Press **Enter** when asked where to save the key, and press **Enter** again twice when asked for a passphrase, leaving it empty.

    This key is used to help the `cluster_action.sh` script (provided with the client software) to run with the servers.

- Find where you noted down the IP address of the server machine, and run this command in a terminal on the **client** to copy the key to the server (replace `<remote ip>` with the **server's** IP address):

    ```bash
    ssh-copy-id -i ~/.ssh/id_rsa.pub <remote ip>
    ```

    You will be asked if you want to continue connecting. Type `yes` and press **Enter**. You will be asked for the server Pi's password which will be the default password of `raspberry`.

    This completes preparation of the client and server. We now need to check everything is correct and working properly with a single server.
