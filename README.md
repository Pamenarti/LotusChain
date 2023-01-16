## PRW -  Lotuscoin Core integration/staging tree (yes tree)

This is the ultra-stable backbone full node and wallet for lotuscoin,
the project aiming to be the longest lived and cheapest public blockchain.  

> openssl version
OpenSSL 1.1.0g  2 Nov 2017

If you have OpenSSL v. 1.0.x please use the "lotuscoin-openssl-1.0" version of this repository located here:  
http://github.com/Pamenarti/lotuschain-openssl-1.0.git

The Lotuscoin block chain is a log structured database.
The money supply is logarithmic.
The unit is log.

## Technical Details:
```
* RPC Port = 9338

* P2P Ports = 8338 (testnet 18338)

* In Wallet mining/logging = Console, "setgenerate true"

* 120 Second Block Target, Diff Retarget every 1 hour

* 30 Confirms for spendable-coins

* Block reward = Harmonic Series

* 1000000/nHeight logs  (after first 100 blocks which form unspendable forest of 5187377 logs) 

* Money Supply = 1000000*(log(nHeight) + gamma)     gamma=Euler-Mascheroni constant 

* ECDSA curve: X9_62_prime256v1 

* Algo = Pure Skein2 (double skein) Bruce Schneier is a lumberjack and NSA didn't choose this algo.
```
## Build Instructions

You will need these dependencies or equivalent:

```
sudo apt-get install git build-essential libboost-all-dev libssl-dev qt-sdk libdb-dev libdb++-dev libminiupnpc-dev libqrencode-dev 
```

Get the source with this command:
```
git clone https://github.com/Pamenarti/lotuschain.git
```

## This project is a fully armed and operational bitcoin-core ported to the lotuscoin network.  

Dedicated to Sipa, Nullc, and Coblee.  Props and Kudos.  

Three tasks have made this port complete:

1) Skein2 hash function for Proof Of Work inserted
2) prime256r1 for ECDSA signatures (including backport to OpenSSL and removal of libsecp256k1)
3) Logarithmic supply curve for long-term economics

Voila - we now have a segwit-enabled lotuscoin client in place for those who would like to use it.


https://github.com/Pamenarti/lotuschain.git

Other clients including Lotuscoin-minimal and Fo-Realz-Lotuscoin are also available.  

## Mining (lotuscutting)

To start lotuscutting with lotuscoind, simply launch it like this: 
```
./lotuscoind setgenerate true
```
For the graphical client, simply go into the debug window (under Help) and type:

```setgenerate true```

contact :
~Paro, (c) 2019 (discord id : Paro#7842)


