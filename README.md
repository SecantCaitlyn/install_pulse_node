

# Installing and Running Pulse Node with the option to add the lighthouse-validator

This guide will help you install and run the Pulse Node using the provided `setup_pulse_node.sh` script.

donations accepted so I might be able to work on mainnet too 😃

erc20: 0xCB00d822323B6f38d13A1f951d7e31D9dfDED4AA

## Prerequisites

- A Unix-based operating system (e.g., Ubuntu, Debian)
- Git installed

## - Installation Steps -

### 1. Install the GitHub client** (if not already installed) 

To install the GitHub client on a Unix-based system, you can use the package manager specific to your operating system. For example, on Ubuntu or Debian, you can use the following command:

   ```bash
   sudo apt-get install git
   ```
### 2. Clone the repository

Open the terminal and navigate to the directory where you want to download the repository. Then, use the following command to clone the repository:

```bash
  git clone https://github.com/tdslaine/install_pulse_node
```
### 3. Change directory

Change to the `install_pulse_node` directory:

```bash
  cd install_pulse_node
```

### 4. Modify script permissions

Give execution permissions to the `setup_pulse_node.sh` script:

```bash
  chmod +x setup_pulse_node.sh
```

### 5. Run the script

Finally, run the `setup_pulse_node.sh` script:
```bash
  sudo ./setup_pulse_node.sh
```
# - Launching, Logging and Stopping the Execution, Beacon and Validator Docker-Containers -

## Launching:

You need to run each `start_###.sh` script once. After doing so, the Docker container should automatically restart on reboot or crashes.

```bash
./start_execution.sh
./start_consensus.sh
./start_validator_lh.sh
```

## Logging:

To view the log files for the execution, beacon, and validator after a reboot you can use the provided log_viewer.sh script or use sepperate commands in a terminal window:

### via script:

make the script executable:

```bash
sudo chmod +x log_viewer.sh
```
run the script:

```bash
./log_viewer.sh
```

### single commands:
```bash
sudo docker logs -f execution
sudo docker logs -f beacon
sudo docker logs -f validator
```

## Stopping Containers:

To stop the containers, you can use the stop_remove_images.sh script provided.

### via script:

make the script executable:

```bash
sudo chmod +x stop_remove_images.sh
```

run the script:
```bash
./stop_remove_images.sh
```

### singel commands:

```bash
sudo docker stop execution
sudo docker stop beacon
sudo docker stop validator
```

Once the containers are stopped, you might need to prune/clean the cache using the command:

```bash
sudo docker container prune
```

## - Updating the Docker-Images should pulse-devs update clients etc. -

To update your Docker containers and images using the watchtower.sh script, follow the steps below:

### 1. Make the script executable: 

To make the watchtower.sh script executable, navigate to the directory where the script is located and run the following command:

```bash
   chmod +x watchtower.sh
```

### 2. Run the script: 

```bash
   ./watchtower.sh
```
### 3. Review the output: 

The script will automatically check for updates and update the necessary containers and images. Review the output of the script to ensure that the update process was successful.

### Please note that the watchtower.sh script might require administrative privileges to execute, depending on your system's settings. If necessary, use sudo to run the script with elevated privileges:

``` bash
   sudo ./watchtower.sh
```
### Ressources:

Pulse:

official gitlab: https://gitlab.com/pulsechaincom

validator launchpad: https://launchpad.v3.testnet.pulsechain.com/en/overview

pulsedev telegram: https://t.me/PulseDEV

Other:

ssh: https://www.digitalocean.com/community/tutorials/how-to-harden-openssh-on-ubuntu-20-04

ssh-tunneling (usefull for secure RPC acces, would be port 8545): https://linuxize.com/post/how-to-setup-ssh-tunneling/

ufw (firewall): https://www.digitalocean.com/community/tutorials/how-to-set-up-a-firewall-with-ufw-on-ubuntu-20-04

tmux: https://tmuxcheatsheet.com/
