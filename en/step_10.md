# Using the completed the OctaPi for the first time

1. Ensure that the dedicated Wi-Fi router, client and OctaPi servers are all powered up. It's best to power up Wi-Fi the router well in advance so that you can be sure it is fully booted before the OctaPi client and servers attempt to log into it.

1. On the **client** machine, open a terminal

    ![Open a terminal](images/terminal.png)

1. Try runnning the "compute.py" example software again by typing the following command:

    ```bash
    sudo python3 compute.py
    ```

    If the OctaPi is working correctly, you will see all the servers being used to run the jobs and being listed in the table at the end of the run.


1. Try runnning the `compute_pi_efficient.py` example software


    ```bash
    sudo python3 compute_pi_efficient.py 1000 100000
    ```

    If the OctaPi is working properly, you can start to do useful calculations, like this estimation of the value of Pi using the 'dartboard' method.

    ![Pi calculation on OctaPi](images/octapi-screenshot.png)
