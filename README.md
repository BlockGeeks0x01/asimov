# Asimov

Official Go implementation of the Asimov protocol https://asimov.network

# Getting Started With Asimov

This document will introduce how to develop simple contracts and
deploying to Asimov blockchain in few minutes.

# Try Asimov

Your can start a solo instance of asimov node for the usage of
development. The following programs is currently available for macOS and
Linux.

- Asimov Full Node ```asimovd```

## Asimov Full Node

Download the package from https://https://asimov.network/wallet , where
there is a link named 'Download Asimov Fullnode'

This zip file contains six parts

- Full Node ```asimovd```

- Tool ```wallet```

- Readme `README.md`

- Sample Configuration `asimovd.sample.conf`

- Genesis block `testnet.block`

- Check Sum `md5.md`

## Prepare Workspace

It requires a directory to run asimovd node, and to store data. The
block chain takes several GB, so this location must have a lot of free
space.

The default is ~/.asimovd on POSIX OSes, $LOCALAPPDATA/Asimovd on
Windows, ~/Library/Application Support/Asimovd on Mac OS, and
$home/asimovd on Plan9. Environment variables are expanded so they may
be used.  NOTE: Windows environment variables are typically %VARIABLE%,
but they must be accessed with $VARIABLE here. Also, ~ is expanded to
$HOME path.

You can also use a self defined directory, which was already created.

<a name="RunNode" />

## Run the node:

Run the node on default workspace
```sh
./asimovd
```

Run the node on self defined directory
```sh
./asimovd homeDir <Your Dir>
```

Then, you may see some error like this
`
Check the config file <Your Dir>/Asimovd/asimovd.conf:
stat <Your Dir>/Asimovd/asimovd.conf: no such file or directory
`
It means you need make a configuration file for the node.

### Config ```asimovd.conf``` in your working path.

Copy sample config file
```sh
cp asimovd.sample.conf asimovd.conf
```

Edit config file
```sh
; devnet,testnet,regtest,simnet
testnet=1
; solo,poa,satoshiplus
consensustype=satoshiplus
privatekey=<your_privatekey_can_generate_by_wallet>
; rpc port
rpclisten=:18334
```


### Config ```genesis.json``` in your working path.

Copy sample json file
```sh
cp genesis.sample.json genesis.json
```

Edit config file in testnet or mainnet, use a same value in all nodes.
```sh
  "collectHeight":204,
  "chainStartTime":1576221900
```

### Copy genesis block into the working path

genesis blocks are located in ./genesisbin/

## Generate your private key.

Build genkeys and generate your private key

```sh
cd cmd
go build
./wallet -c genKey -n test
  New key pair (priv, pubkey) (format:hex)
      { 0xf57dcd236c78368d64eb455b35d98c6d676394a1bb246f88fddd4d9103132729 , 0x020e470848be43cc2a9927af3ea9919e36a1e1b3319bc3845a31e1dcb5bcde79b8 }
      Compressed pubkey hash address: 0x664ceee539d3d5314824750b5f164cd8f8f87109b4
  Bitcoin base58check encode secret:  cVouSDdm3zVvTg5DuBqFaatghYQ1cApyEYBSdoSAyscmTCB5CK55
  Bitcoin legacy type address:  mnXjqNr44AbA5HbxbySBqf7b8Ho37Wqpv6
  Bitcoin p2sh-segwit type address:  2N1unojExgURPZ56sgwHetWVMsWqFPZD2wS
  Bitcoin bech32 type address:  tb1qfnhw2wwn65c5sfr4pd03vnxclru8zzd50s8fcy
```

## Source code Project

### Clone Source code

```sh
go get github.com/AsimovNetwork/asimov
```

### Install Dependencies:

```sh
govendor sync
```

### Prepare config

Same as above configuration section.

## Toolchain

Clone and build

```sh
git clone https://github.com/AsimovNetwork/developer.git
npm install
npm run serve
```

Or visit online [Developer Center](https://developer.asimov.network) to use
the web IDE for asimov blockchain contract development.


## Start the node

After prepare workspace and configuration. Now you can [start the node](#RunNode)


## Cleanup

You can cleanup the state data when you want to reset all the states of
the test blockchain.

```sh
# stop asimovd
cd <Your Dir>/Asimovd/
rm -rf data state logs
# restart asimov
```

## Asimov Testnet

Asimov Testnet is now available for developers.

Every one can connect the testnet with AsiLink and Web IDE.

# Wallet and Account

Using [AsiLink](https://www.asimov.network/wallet) Chrome Extension to
manager your wallet and account.

