# Geth-and-Prysm-Docker
A docker-compose file to quickly spin up an Ethereum PoS node
# Configuration
Before starting the container, there are a few things to configure in `docker-compose.yml`, errors WILL be thrown if you do not edit these.
* On lines 17 and 55 under `volumes`, replace `<PATH-ON-HOST>` with either a docker volume, or a path to mount the volume to on the host.<br>
  * For Example: `${HOME}/eth-data` would mount the data directory to home in a dir named `eth-data`
* On line 66 in the flag `--p2p-host-ip` replace `<HOST-IP-HERE>` with the host machines IP.<br>
  * This can be found quickly with the following command: `curl ifconfig.io`
  * This flag is not a hard requirement, so can be removed if necessary. But it is reccomended to be a good peer to the network
* On line 64, in the flag `suggested-fee-recipiant`, put your ETH wallet address in
 
 # Run
 To run the container, simply run the command `docker-compose up -d` from within the same directory your `docker-compose.yml` is in
 
# Firewall & Port Forwarding
In order to have a secured, but reachable node, it is important to make the following changes in both your hosts firewall, and your networks router. A more complete list of firewall security best practices check out [Prysm's port and firewall page](https://docs.prylabs.network/docs/prysm-usage/p2p-host-ip)
* Firewall
  * Port 8445: DENY
  * Port 3500: DENY
  * Port 8551: DENY
  * Port 4000: DENY
  * Port 12000: ALLOW
  * Port 13000: ALLOW
  * Port 30303: Allow
* Port Forwarding
  * Open Port 12000 UDP
  * Open Port 13000 TCP
  
# Credits
Parts of Geth's docker-compose was from [islishude's excilent repo](https://github.com/islishude/geth-docker)
Thanks to both the Geth and Prysm discord communities for all the help when I was setting up.<br>
[Geth Discord](https://discord.gg/V2Xrze2p)<br>[Pyrsm Discord](https://discord.gg/prysmaticlabs)
