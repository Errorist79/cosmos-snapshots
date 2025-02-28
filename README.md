# cosmos-snapshots  
List of snapshots:   
http://135.181.60.250/      - Akash Network (Mainnet) truncated via statesync  
http://135.181.181.121/akash/  
http://135.181.181.119/akash/  
http://135.181.181.123/akash  
http://135.181.181.122/akash  

http://135.181.60.250:8081/ - Sifchain (Betanet) truncated via statesync  
http://135.181.60.250:8083/ - Sentinel (Mainnet truncated via statesync   
http://135.181.60.250:8084/ - Desmos (Mainnet) truncated via statesync  
http://135.181.60.250:8086/ - Stargaze (Mainnet) truncated via statesync  
http://135.181.60.250:8087/ - Agoric (Mainnet) truncated via statesync   
http://snapshots.alexvalidator.com/oasis/ - Oasis (Mainnet)    
http://snapshots.alexvalidator.com/ixo/ - IXO (Mainnet)   
http://snapshots.alexvalidator.com/regen/ - Regen (Mainnet)   
http://snapshots.alexvalidator.com/stargaze/ - Stargaze (Mainnet)   
https://snapshots.stakecraft.com/ - Juno (Mainnet)  
https://cosmos-snap.staketab.com/ixo - IXO (Mainnet)  
https://cosmos-snap.staketab.com/stargaze - Stargaze (Mainnet)  
https://cosmos-snap.staketab.com/sifchain - Sifchain (Betanet)  
https://cosmos-snap.staketab.com/comdex - Comdex (Mainnet)  
https://cosmos-snap.staketab.com/axelar - Axelar (Mainnet)  
https://mercury-nodes.net/kichain-snaps/ - Kichain (Mainnet)  

[Akash snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Akash.md)  
[Agoric snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Agoric.md)  
[Sifchain snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Sifchain.md)  
[Sentinel snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Sentinel.md)  
[Desmos snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Desmos.md)   
[Oasis snapshot instruction](https://github.com/Bambarello/cosmos-snapshots/blob/main/Oasis.md)  
[Stargaze snapshot instruction](https://github.com/c29r3/cosmos-snapshots/blob/main/Stargaze.md)    
[Kichain snapshot instruction](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/kichain.md)  
[IXO snapshot instruction(Staketab)](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/ixo.md)  
[Sifchain snapshot instruction(Staketab)](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/sifchain.md)  
[Stargaze snapshot instruction(Staketab)](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/stargaze.md)  
[Comdex snapshot instruction(Staketab)](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/comdex.md)  
[Axelar snapshot instruction(Staketab)](https://github.com/staketab/nginx-cosmos-snap/blob/main/docs/axelar.md)  

## MIRRORS  
http://rpc01-skynet.paullovette.com/ - provided by Paul Lovette  
http://162.255.116.68/snapshots/ - privded by Min (Min#6706)  
https://snapshots.stakecraft.com/    - provided by Alex Novy  
http://snapshots.alexvalidator.com/  - provided by Alex [(Bambarello) Validator](https://github.com/Bambarello)  
- Oasis
- Stargaze
- Regen
- IXO  
- Sentinel  
  
https://cosmos-snap.staketab.com/  - provided by Staketab  
  
https://snapshots.stake2.me/ - provided by [Danil Ushakov](https://github.com/k0kk0k)  
- Agoric
- Akash
- Certik
- Gravity bridge
- IXO
- Osmosis
- Sifchain
- Stargaze


https://snapshot.notional.ventures/ - provided by [Notional](https://github.com/notional-labs)
- Cosmoshub
- Osmosis
- Juno
- Starname
- Regen
- Akash
- Sentinel
- E-money
- Terra
- Ixo
- Sifchain
- Likecoin
- Kichain
- Cyber
- Cheqd
- Stargaze
- Band
- Chihuahua
- Kava
- Bitcanna
- Konstellation
- Omniflixhub
- Vidulum
- Provenance
- Dig
- Gravity bridge
- Comdex
- Cerberus
- Bitsong
- AssetMantle
- FetchAI

## Run your own backup server with snapshots  
Install requirements  
```bash
sudo apt update && \
sudo apt install curl git docker.io -y
```

Clone github repo  
`git clone https://github.com/Errorist79/cosmos-snapshots.git`  

Create folder for snapshots  
`mkdir $HOME/kyve_snap`

Start Nginx via docker  
```bash
cd $HOME; \
docker run --name nginx \
--restart always \
-v $(pwd)/default.conf:/etc/nginx/conf.d/default.conf \
-v $(pwd)/kyve_snap/:/root/ \
-p 80:80 \
-d nginx
```

Fill in the variables in the file `akash_snapshot.sh`  
```
CHAIN_ID="korellia"
SNAP_PATH="$HOME/kyve_snap"
LOG_PATH="$HOME/akash/kyve_log.txt"
DATA_PATH="$HOME/.kyve/data/"
SERVICE_NAME="kyved.service"
```
Create new snapshot  
`./kyve_snapshot.sh`  

Check snapshot  
```bash
MY_IP=$(curl -s 2ip.ru); \
curl -s http://${MY_IP}
```

## Automation  
You can add script to the cron  
```cron
# start every day at 00:00
0 0 * * * /bin/bash -c '/root/akash_snapshot.sh'
```
