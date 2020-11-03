## Set up one OctaPi server

Each of the Raspberry Pi 3 computers in the cluster needs to have its own micro SD card prepared. However, as each card is identical, you can set up just one server, check it's working, and then replicate the SD card for the other servers.

- On a new micro SD card, install the latest version of Raspbian by following the [software guide instructions](https://www.raspberrypi.org/learning/software-guide/quickstart/){:target="_blank"}.

- Boot up a Raspberry Pi 3 or 4 using this SD card with a keyboard, screen, and mouse connected.

- Ensure the Raspberry Pi is connected to the internet.

- Open a terminal.

![Open a terminal](images/terminal.png)

- As with the client, install `dispy` by typing this command into the terminal:

```bash
sudo pip3 install dispy
```

- Install `psutil` by typing this command into the terminal:

```bash
sudo pip3 install psutil
```

`dispy` uses `psutil` for reporting CPU usage of the servers in the cluster.

- Ensure you are in the `/home/pi` directory by typing `cd /home/pi`.

- If you are using the Unicorn HATs, install the software for them by typing this command into the terminal:

```bash
curl https://get.pimoroni.com/unicornhat | bash
```

You will need to restart your Pi afterwards.

Then, reopen the terminal and make sure you are in the `/home/pi` folder by typing `cd /home/pi`.

Download the `start_unicorn.sh` bash script for installation on the server using this command:

```bash
wget https://raw.githubusercontent.com/raspberrypilearning/octapi-setup/master/server/start_unicorn.sh
```

Make the script executable by typing this command:

```bash
chmod u+x ./start_unicorn.sh
```

- Next you need a script to start a dispynode, running at boot on the server. In your terminal type the following:

```bash
nano start_dispynode.sh
```

- When nano starts you can add the following lines of code:

```bash
#!/bin/sh -e
sleep 30
_IP=$(hostname -I)
dispynode.py -i $_IP --daemon
```

This script will:
1. sleep for 30 seconds to allow the server to connect to the network, get your server's IP address
2. fetch the server's IP address
3. start a dispynode daemon that will listen out for instructions from your client.

- Press `Ctrl` + `o` to save your changes, then `Ctrl` + `x` to exit the nano editor.

- Make the script executable.

```bash
chmod +x start_dispynode.sh
```

Now you need this script to start when the server boots. To do this you can use `crontab`

- In a terminal type:

```bash
crontab -e
```

- Scroll to the bottom of the file and then add the following line.
```bash
@reboot sudo /home/pi/start_dispynode.sh
```

- Check that remote login via SSH is enabled so that remote command line access to your server is possible. In the **Preferences** menu, select **Raspberry Pi Configuration**.

![Enable SSH](images/enable-ssh1.png)

Then click on the **Interfaces** tab and make sure that SSH is enabled.

![Enable SSH](images/enable-ssh.png)

