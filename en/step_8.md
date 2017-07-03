# Check that it works

- Make sure your dedicated "OctaPi" router is powered on and fully booted up, the **client** is booted with peripherals attached, and the **server** is booted with only a power lead attached.

- Open a terminal on the **client**

    ![Terminal](images/terminal.png)

- Make sure you are in the `/home/pi` directory and type the following command to run the `compute.py` example software provided with the client software examples you downloaded earlier:

    ```bash
    sudo python3 compute.py
    ```
    The `compute.py` Python script runs 15 jobs on your server. They are all just random delays before returning. If the OctaPi is working correctly, the jobs will complete in about a minute and a table showing the statistics for the application will be shown in the terminal. You should see a result similar to this:
    
    ```bash
    
                               Node |  CPUs |    Jobs |    Sec/Job | Node Time Sec
    ------------------------------------------------------------------------------
     192.168.1.3 (raspberrypi)     |     4 |       16 |     12.841 |        205.460
    
    Total job time: 205.460 sec, wall time: 57.347 sec, speedup: 3.583
    ```


    If the `compute.py` script does not work, review your steps one by one and check that client, server, and router are all set up correctly and working properly.

- If the test worked, use the client to manually shut down the server (replacing `<remote_ip>` with the IP address of the **server** you noted down earlier):

    ```bash
    ssh <remote_ip>
    sudo shutdown -HP now
    ```

    You may need to use **nmap** again to find the server IP address if it changed when the Wi-Fi router rebooted.

    In future we will be using the `cluster_action.sh` script to do this.

- Once the server is shut down, remove its micro SD card.

- Using an SD card duplicator or a computer which is able to read SD cards, create seven more identical copies of this SD card and insert them into the other servers so that you have a total of eight.

**NOTE:** It is also possible (but time consuming) to create your eight SD cards by following the server setup instructions eight times. If you choose to use this method instead of duplicating the SD card image, you must run the `ssh-copy-id` command on the client once per server to copy the key across to each server separately. DO NOT REGENERATE THE KEY.
