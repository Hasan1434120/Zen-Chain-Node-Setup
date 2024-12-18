## Zen-Chain-Node-Setup

Lütfen beğeni ve fork unutmayın


1-Musluğa erişim kazanmak için önce bekleme listesine katılın: 
https://www.zenchain.io/waitlist adresini ziyaret edin

2-Bekleme listesine kaydolduktan sonra musluğu buradan talep edin: 
https://faucet.zenchain.io/

# Kurulum:
 1- Sistem Güncelle:

  ` sudo su`

  ` apt update`

  ` sudo apt install -y curl wget tar jq git`

  2- Docker'ı yükleyin (eğer yüklü değilse):

  `apt install docker.io -y`

  3- Klasör Oluşturun ve İzinleri Ayarlayın:

  `mkdir -p "$HOME/chain-data"`
  `chmod -R 777 "$HOME/chain-data"`

  4-Düğümü Çalıştırın : (YOURVALIDATORNAME ifadesini istediğiniz ifadeyle değiştirin )

  ```
docker run \
    -d \
    --name zenchain \
    -p 9944:9944 \
    -v "$HOME/chain-data:/chain-data" \
    ghcr.io/zenchain-protocol/zenchain-testnet:latest \
    ./usr/bin/zenchain-node \
    --base-path=/chain-data \
    --rpc-cors=all \
    --rpc-methods=unsafe \
    --unsafe-rpc-external \
    --name=YOURVALIDATORNAME \
    --bootnodes=/dns4/node-7242611732906999808-0.p2p.onfinality.io/tcp/26266/p2p/12D3KooWLAH3GejHmmchsvJpwDYkvacrBeAQbJrip5oZSymx5yrE \
    --chain=zenchain_testnet
`

    5-
