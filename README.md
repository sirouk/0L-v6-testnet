# Notes
```
# Built upon the concepts from our 0L v6 Makefile: 
https://github.com/0LNetworkCommunity/libra/blob/v6/Makefile
```

# Usage

## Prepare
```
cd ~
git clone https://github.com/sirouk/0L-v6-testnet
cd ~/0L-v6-testnet
echo GITHUB_TOKEN='...' > .env
```

## Build
```
# build one image first so other images can reuse it's image layers (takes a bit of time)
sudo docker-compose build alice

# build the rest (much faster)
sudo docker-compose build
```

## Run alice/bob/carol (build, register, and start testnet)
```
sudo docker-compose up -d

# check on the containers
sudo docker ps -a

# connect to a running container
sudo docker attach 0l-devnet_alice_1
sudo docker attach 0l-devnet_bob_1
sudo docker attach 0l-devnet_carol_1

# check the testnet registration
https://github.com/0LNetworkCommunity/dev-genesis
```

## Tests/Troubleshooting
```
# STARTUP
# start individually
# start alice
sudo docker-compose up alice

# start bob
sudo docker-compose up bob

# start carol
sudo docker-compose up carol


# EDITING/TESTING

# edit the dockerfile
sudo nano docker/Dockerfile

# edit the docker-compose.yaml
sudo nano docker-compose.yaml

# stop everything, rebuild alice, and start alice
sudo docker-compose down && sudo docker-compose build alice && sudo docker-compose up alice

# stop everything, rebuild everything, and start everything (start testnet)
sudo docker-compose down && sudo docker-compose build && sudo docker-compose up -d


# NUKE the containers, rebuild, and restart everything (slow)
sudo docker-compose down && sudo docker rm $(sudo docker ps -a) && sudo docker rmi $(sudo docker image ls) && sudo docker-compose build && sudo docker-compose up -d

```
