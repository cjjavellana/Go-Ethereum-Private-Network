# 3-Node Ethereum Private Network in a Box
Please refer [here](https://geth.ethereum.org/docs/interface/private-network) for the manual setup & configuration process


## Prerequisites

1. [Vagrant](https://www.vagrantup.com/)
2. [Virtual Box](https://www.virtualbox.org/)

## Ethereum Cluster Details

1. Bootstrap Node - A rendezvous point which all other nodes use to join the network.

2. Member node 1 - A participating node. You may have an unlimited number of them.

3. Clique - The network's transaction signer affirming that each transaction is valid. For a private network, it is recommended to run a proof-of-authority signer.

## Getting Started

1. Clone Project Repository
  
  ``` bash
  $ git clone https://github.com/cjjavellana/Go-Ethereum-Private-Network.git
  ```

  Note: You may need to comment out the `config.ssh.private_key_path = "/home/christian/VirtualBox VMs/go-ethereum/private_key"` in the Vagrantfile.

2. Initialize Virtual Environment & Setup GETH Private Network

  ```bash
  $ vagrant up
  ``` 

3. Verify that your private network is up & running

  In your host
  ```bash
  $ vagrant ssh
  ```

  In the your guest
  ```
  [vagrant@localhost ~]$ ps -ef | grep geth
  ```

## TODOs

1. Install npm & truffle for deploying smart contracts

2. Install MariaDB / Mysql


