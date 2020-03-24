# 3-Node Ethereum Private Network in a Box
Please refer [here](https://geth.ethereum.org/docs/interface/private-network) for the manual setup & configuration process


## Prerequisites

1. [Vagrant](https://www.vagrantup.com/)
2. [Virtual Box](https://www.virtualbox.org/)

Before provisioning this Virtual Box, ensure that the following ports (in your host OS) are available:
1. 3306 - MySQL Database
2. 8545 - GETH JSON RPC Port
3. 8546 - GETH WS Port

## Ethereum Cluster Details

1. Node 1
   > API Server
     As an API Server, this node exposes the following ports:
     8585 - JSON RPC Port
     8546 - Websocket
          
   > Bootstrap Node - A rendezvous point which all other nodes use to join the network.
     Exposes p2p port 30303     

   > Clique - The network's transaction signer affirming that each transaction is valid. For a private network, it is recommended to run a proof-of-authority signer.

2. Member node 2 - A participating node. You may have an unlimited number of them.

## Getting Started

1. Clone Project Repository
  
  ``` bash
  $ git clone https://github.com/cjjavellana/Go-Ethereum-Private-Network.git
  ```

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

## MySQL

A MySQL database server is also provisioned in this box. Details are as follows:

Host: localhost (port forwarded)
Port: 3306
Username: blockchain
Password: blockchain

## Deploying Smart Contracts
TODO

## TODOs

1. Install npm & truffle for deploying smart contracts


