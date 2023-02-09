# Usage

## Prepare
```
echo GITHUB_TOKEN='...' > .env
```

## Build
```
# build one image first, so other images can reuse it's image layers
sudo docker-compose build alice
# build the rest
sudo docker-compose build
```

## Run alice/bob/carol
```
sudo docker-compose up -d
```
