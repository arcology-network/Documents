# Testnet Guide (v0.9.1)

- [Testnet Guide (v0.9.1)](#testnet-guide-v091)
  - [1. Introduction](#1-introduction)
  - [2. Getting Started](#2-getting-started)
  - [3. Release](#3-release)
  - [4. Prepare the Hosting Machines](#4-prepare-the-hosting-machines)
  - [5. Set up the Testnet](#5-set-up-the-testnet)
  - [6. Login to the Docker Image](#6-login-to-the-docker-image)
  - [7. Start Ammolite](#7-start-ammolite)
  - [8. Choose the Test Cases](#8-choose-the-test-cases)

## 1. Introduction

The client software consists of multiple network services that can be deployed on multiple machines to achieve optimal performance. One of implications this type of design is increased complexicity. The testnet suite is a package containing all the necessary librares, python scripts and binary installers to make deployment and testing process easiler.

The suite is designed to facilitate these tasks:

1. **Deploy a testnet**
2. **Interact with the testnet**

Users with knowledge of python and blockchain should be able to start a testnet and take test runs with little effort.

## 2. Getting Started

A client has of a number of network services communicating through MQ and RPC. These services can be deployed on multiple machines to achieve better performance. The whole installation process consist of the following major steps.

![alt text](/img/installation-steps.png)

## 3. Release

You can download the latest testnet installer [here](https://github.com/arcology-network/benchmarking/releases) 

## 4. Prepare the Hosting Machines

1. [On AWS](https://github.com/arcology-network/aws-ansible)
2. On Premises

Once hosting machines are ready, you can start to set up the testnet

---

## 5. Set up the Testnet

The hosting machines are ready by now, the next step is to set up node clusters on the hosting machine.
The [deployment](https://github.com/arcology-network/deployments) project contains a set of tools to automate the process. Once testnet is live, it is ready to process transactions.  

## 6. Login to the Docker Image

The docker container has all necessary modules included to interact with the network. First, you need to login to the container.

```shell
ssh -p 32768 root@[Your docker's host IP]
```

- **Username**:   root
- **Password**:   frY6CvAy8c9E

The next step is to check the connection to the node cluster. You can find you frontend serivce ip from **testnet.json** file.

```python
$ python ./checkStatus.py [The frontend service ip]
```
---

## 7. Start Ammolite

To use [Ammolite](https://github.com/arcology-network/ammolite), just start Python **in the docker image and import all necessary modules.**

## 8. Choose the Test Cases

The follow cases can run both interactively and programmatically.

- [Token transfer](https://github.com/arcology-network/parallel-coin-transfer)
- [Parallelized CryptoKitties](https://github.com/arcology-network/parallel-kitties)
- [Parallelized dstoken](https://github.com/arcology-network/parallel-dstoken)
  
> Please wait for one script to complete before starting the next one. The best way to tell is by looking at the number of transactions contained in the lastest block. The system has processed all transactions once it drops to zero(not rising from zero which shows the system is picking up speed).
