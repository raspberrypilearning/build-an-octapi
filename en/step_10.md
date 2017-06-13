# Using the completed OctaPi for the first time

- Ensure that the dedicated Wi-Fi router, client, and OctaPi servers are all powered up. It's best to power up the Wi-Fi router well in advance so that you can be sure it is fully booted before the OctaPi client and servers attempt to log into it.

- On the **client** machine, open a terminal.

    ![Open a terminal](images/terminal.png)

- Try running the "compute.py" example software again by typing the following command:

    ```bash
    sudo python3 compute.py
    ```

    If the OctaPi is working correctly, at the end of the run all the servers used to execute the job will be listed in the table.


- Try running the `compute_pi_efficient.py` example software:


    ```bash
    sudo python3 compute_pi_efficient.py 1000 100000
    ```

    If the OctaPi is working properly, you can start to do useful calculations, like this estimation of the value of pi using the 'dartboard' method.

    ![Pi calculation on OctaPi](images/octapi-screenshot.png)
