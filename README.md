# IPFSConsortiumDocker 

IPFSConsortium Docker repo

## Getting Started

These instructions will get you a copy of the project up and running on your local machine.

### Prerequisites

- git

   Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

   Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding current user to docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

   Install [docker-compose](https://docs.docker.com/compose/install)
   
**Note**: Make sure you can run `git`, `docker ps`, `docker-compose` without any issue and without sudo command.

## Running

```
$ git clone https://github.com/ipfsconsortium/IPFSConsortiumDocker.git
$ cd IPFSConsortiumDocker
```

### Start
```
$ docker-compose up -d
```
### Stop
```
$ docker-compose down
```
### Status
```
$ docker-compose ps
```
### Logs
```
$ docker-compose logs -f
```

After it starts ipfs will be accessible from 5001 and 8080 only at localhost (if IPFS_ENABLE=true). For example, the webui will be accessible from (here)[http://localhost:5001/webui]

You can use another IPFS location using the environment variables IPFSAPIHOST and IPFSAPIPORT.

For more information about environment variables [IPFSConsortiumProxy](https://github.com/ipfsconsortium/IPFSConsortiumProxy)

### Run commands
```
$ docker-compose exec ipfsconsortium ipfs ...
```

## How does the consortium work ?

The consortium is managed by a smart contract deployed here 

* Livenet `0x7433c7c768be4025ab791fb7b2942c3d9e309f3e` ( startblock 4090116 )
* Rinkeby `0x3ef882ffcE8fC40f6Ca473f29AC16dE8a60419BB` ( startblock 1846107 )

## How can I join the consortium ?

* Go to the IPFSConsortium chat on Riot ( see below ) and ask for access
* OR: Deploy your own version of the contract, and start your own consortium

## How can I help support the IPFS consortium ?

### Running an IPFS node

Setup a local IPFS node + Ethereum node , install the script and start listening to one or more IPFS consortium contracts

### Contributing to the development

We use ZenHub as a project management tool for this project.

- Install the ZenHub chrome plugin ( https://chrome.google.com/webstore/detail/zenhub-for-github/ogcgkffhplmphkaahpmffcafajaocjbd )
- visit the project board : https://github.com/ipfsconsortium/pm/issues/2#boards?repos=106814113
- check the `backlog` and `new issues` pipeline 

If you don't want to install this plugin , just check the issues on the project 

# Get in touch

- IPFSConsortium chat on Riot: https://riot.im/app/#/room/#ipfsconsortium:matrix.org
