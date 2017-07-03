## Controlling the cluster

Now that you have checked your OctaPi is set up and running correctly, you can use the `cluster_action.sh` script to control it.

The `cluster_action.sh` script runs on the client and uses SSH to administer the servers (that's why we used `ssh-keygen` to authenticate the client with the servers). It relies on the correct IP addresses of the servers being listed in the `ip_list` file. It is a good idea to delete the `ip_list` file when booting the cluster for the **first time** so that the list is regenerated.

- From a terminal, type the following command to remove the `ip_list` file:

  ```bash
  rm ip_list
  ```

### Setting up the cluster_action script
- On the client machine, open a terminal

- Make sure you are in the `/home/pi` directory by typing in `cd /home/pi`

- Set the permissions for the cluster action script so that you can run it by typing this command:

  ```bash
  chmod u+x ./cluster_action.sh
  ```

### Ensure the client can recognise each server SSH key



The first time you use the cluster, you may need to manually 'ssh' into each server from the client so that the client recognises each server ssh key properly (be sure to replace `<ip address of server>` with the actual server IP address).

```bash
ssh <ip address of server>
```

If at all, this will only be needed once.

### Options for the cluster_action script

The following options are available as parameters accepted by the script:

**reboot** – reboots all the servers (the client and router are ignored)

Example:

```bash
./cluster_action.sh reboot
```

**shutdown** – shuts down each server and places it into a safe state. If a server is not shut down correctly, it may cause the micro SD card to be corrupted and lead to the processor failing to boot when next used.

Example:

```bash
./cluster_action.sh shutdown
```

**date** – distributes the client date and time (to the nearest minute) to each server. The Raspberry Pi 3 does not have a real-time clock, so the correct time will need to be set on the client first.

Example:

```bash
sudo date -s "11 Apr 2017 12:42"
./cluster_action.sh date
```

**unicorn** – invokes the unicorn script on each server and passes it the name and location of a Pimoroni Python script as a parameter. For this to work you need to have `start_unicorn.sh` in `/home/pi` on each server as described earlier.

Example:

```bash
./cluster_action.sh unicorn /home/pi/Pimoroni/unicornhat/examples/random_sparkles.py
```
