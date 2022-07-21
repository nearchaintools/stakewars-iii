# stakewars-iii

## Cloud Provider 
- Hetzner Hosting for 80$/month. 
- HW: 120GB RAM, Intel Core i9000, 1TB SSD

## Setup
- folow https://github.com/near/stakewars-iii/tree/main/challenges

## Hard Fork

```
cp ~/.near/node_key.json ~
cp ~/.near/validator_key.json ~
rm -rf .near
cd nearcore
./target/release/neard --home ~/.near init --chain-id shardnet --download-genesis
rm ~/.near/node_key.json
cp ~/node_key.json ~/.near/
cp ~/validator_key.json ~/.near/
rm ~/.near/config.json
wget -O ~/.near/config.json https://s3-us-west-1.amazonaws.com/build.nearprotocol.com/nearcore-deploy/shardnet/config.json
sudo systemctl stop neard
git pull
git checkout 8448ad1ebf27731a43397686103aa5277e7f2fcf
cargo build -p neard --release --features shardnet
./target/release/neard --home ~/.near run
```
