#

## Identify the Network Interfaces

```sh
ip addr
```

Look for the interface connected to your network (e.g., eth0, enp0s3, etc.).

1. Create a new network configuration file:

   ```sh
   sudo nano /etc/systemd/network/static-your-interface.network
   ```

   {static-your-interface} can what ever you want to name the file just be sur to use .network as a prefix

2. Add the following configuration:

   ```sh
   [Match]
   Name=your-interface

   [Network]
   Address=192.168.1.xxx # your static ip address
   Netmask=255.255.255.xxx # your netmask
   Gateway=192.168.1.xxx # your gateway
   DNS=8.8.8.8 8.8.4.4 # or your DNS servers
   ```

3. Enable and Restart systemd-networkd:

   ```sh
   sudo systemctl enable network
   sudo systemctl restart network
   ```

4. Verify the Configuration:
   ```sh
   ip addr show your-interface
   ```
