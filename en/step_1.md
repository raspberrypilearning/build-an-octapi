# Build an OctaPi

In this resource you will make a distributed computer system using:

- Eight Raspberry Pi 3 computers acting as **servers**
- ...controlled by another Raspberry Pi which is called the **client**

![OctaPi system](images/octapi-system.png)

You can use the power of the 8 server CPUs (32 cores) to execute computations in parallel from the client CPU much more quickly than the client could do on its own. This is known as a **cluster computer**, a kind of cloud computer. In this project you will be able to develop and run applications on the cluster in Python 3 running from the client.

There are three steps you will need to take to make an OctaPi:

1. Create a Wi-Fi network for the cluster using a dedicated router
1. Create a client machine
1. Create eight servers

You don't actually need exactly eight servers as the cluster will work with any number of servers up to limits determined by the performance of your Wi-Fi router, so if you don't have enough Raspberry Pis available to make an OctaPi, why not make a HexaPi (6) or a TetraPi (4)?

If you want to make your cluster look pretty, you can optionally fit Pimoroni Unicorn HAT 8x8 LED arrays to each server. The bash control script on the client machine can be used to change the patterns on the Unicorn HATs.
