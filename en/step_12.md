## Troubleshooting

## When I try and run the `cluster_action.sh` script, I get 'permission denied'.
This file is a bash script and requires execute permission. The error probably occurs because the execute permission is not set for some reason.

- Make sure you are in the `/home/pi` directory by typing `cd /home/pi` in a terminal window.

- Type the following command to make the script executable (there is no need to use `sudo`).

    ```bash
    chmod u+x cluster_action.sh
    ```

## The `ip_list` file only has the router IP and client IP addresses listed - where are the servers?
If you  are seeing unexpected content, or missing content, this is most likely because the client machine is not logged into the OctaPi network when `cluster_action.sh` is run. This can happen if you did not remove other WiFi networks from `/etc/wpa_supplicant/wpa_supplicant.conf`. The client will log into the best available WiFi network, which may not be the OctaPi network.

- To edit the `wpa_supplicant.conf` file, use nano as follows:

    ```bash
    sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
    ```

- The file contents should look like this:

    ```bash
    ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
    update_config=1
    country=GB

    network={
	    ssid="OctaPi"
	    psk="itsasecret"
	    key_mgmt=WPA-PSK
    }
    ```

Remove any 'network { }' sections for other networks, and press `Ctrl` + `o` to save your changes and then `Ctrl` + `x` to exit nano. Reboot the client for the changes to take effect.

## I get messages saying there is 'no route to host' when using the `cluster_action.sh` script.
This can happen if the network connection is unreliable and causes the router to drop an IP address. It can also happen if you have more servers connected to your router than it can handle. Network reliability is affected by how close the router is to the rest of the system and by how many other WiFi networks are present. Try moving the OctaPi router to within a couple of metres of the OctaPi system and/or moving away from other WiFi routers.

## I get 'host key verification failed' messages when I run the `cluster_action.sh` script.
This may happen the first time you run the script because the client hasn't seen the server IP addresses before when performing an SSH login. To fix this, do the following.

- Open a terminal and type in this command to list the IP addresses allocated to your servers:

    ```bash
    cat ip_list
    ```

- Type the following command to find the client's IP address.
    ```bash
    hostname -I
    ```

- Ignore '192.168.1.1', as this is the 'OctaPi' router, and ignore the client IP address which you just found out with the previous command. From the client machine, manually log in to each of the other IP addresses listed via SSH. When you are prompted, say 'yes' to the question to proceed, then type `exit` again.

    ```bash
    ssh <ip_address>
    (say 'yes' to continue)
    exit
    ```

`<ip_address>` is one of the server addresses in the `ip_list` file. You will need to type 'yes' in full. Repeat this for all of the servers.

## The application I am running freezes after a while.
If something goes wrong on a server, either with the operating system or with the Python code running, it can disrupt operation of the whole cluster. This can happen if the jobs running are quite large or if there is a lot of network traffic. Try rebooting the server cluster with `./cluster_action.sh reboot` before defining smaller jobs in your client code.

## The application I am running says 'Ignoring invalid reply for job...'
This can happen if the client and one or more servers have got out of sync, which can be caused by the client code crashing or being interrupted by pressing `Ctrl`+ `c`. It can also happen if one of the servers crashes while in operation.

To fix this, try to determine which bit of code has the error and fix that first. Then reboot the cluster with the `cluster_action.sh` script.

```bash
./cluster_action reboot
```

The servers should all reboot into the same state and be ready to accept jobs from the client. Depending on the condition of the client following a crash, it may also need rebooting.

## When I run my application on the client, I get a message saying a network port is already in use.
This may happen following an error in the client Python code or an exit from the dispy software without closing the cluster. It is caused by a dispy process remaining active on the client (which is capturing the TCP port used for communications with the servers). To correct this problem, reboot the client so that dispy can be cleanly restarted.

## How do I debug Python code running on the servers?
The code you are running is defined on the client and distributed to the servers at run time. However, once the code is on the servers, any errors don't get reported back to the client. If there is a bug in the code once it is running on the server, this can cause the whole cluster to fail. To debug, develop all the code on the client for standalone operation and test it thoroughly before adding the `dispy` code to distribute it to the servers.

## How do I install new Python modules on the OctaPi servers?
If you have installed new Python modules on the client that are needed for the code distributed to the servers, make sure you have also installed the module on every server before attempting to run your code. The `import` statement needs to be inside the function that you will be distributing.

## Will the OctaPi work with a WiFi router that was provided by my broadband service provider?
You need to use a dedicated router to avoid conflicting with other devices. Repurposing a broadband service provider's router can work, but the router might be set to non-default conditions or have locked down features to suit the provider's requirements. This could affect its use with the OctaPi. If you think you may be experiencing networking problems with a repurposed router, try switching to a new WiFi router. We have used a variety of routers, starting at a price around £20, without problems. The router should be able to handle at least nine simultaneous connections if you have a single OctaPi module. The specific router used to test this resource was a TP-LINK TL-WR841N.

## I get networking problems with very large clusters (more than one OctaPi module).
Your WiFi router needs to be able to handle large numbers of simultaneous connections. If it is not, you may start to experience dropped connections to the servers ('no route to host'). In extreme cases, the router may even freeze or reboot unexpectedly. Modern routers for domestic use, even high-performance gaming routers, are not designed for large numbers of simultaneous connections. However, we have observed reliable network performance for two OctaPi modules (17 simultaneous connections) with a router in a £20 price range, and for up to four to five OctaPi modules (max. 41 simultaneous connections) with a gaming router. Beyond that, WiFi networking becomes impractical.
