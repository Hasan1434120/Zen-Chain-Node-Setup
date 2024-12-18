## Zen-Chain-Node-Setup

Lütfen beğeni ve fork unutmayın


1-Musluğa erişim kazanmak için önce bekleme listesine katılın: 
https://www.zenchain.io/waitlist adresini ziyaret edin

2-Bekleme listesine kaydolduktan sonra musluğu buradan talep edin: 
https://faucet.zenchain.io/

# Kurulum:
### 1- Sistem Güncelle:

  ``` sudo su```

  ``` apt update```

  ``` sudo apt install -y curl wget tar jq git```

 ### 2- Docker'ı yükleyin (eğer yüklü değilse):

  ```apt install docker.io -y
  docker run
```

###  3- Klasör Oluşturun ve İzinleri Ayarlayın:

  ```mkdir -p "$HOME/chain-data"```
  
  ```chmod -R 777 "$HOME/chain-data"```

###  4-Düğümü Çalıştırın : 

> ##### (YOURVALIDATORNAME ifadesini istediğiniz ifadeyle değiştirin )

  ```docker run \
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
```

 ###   5-Oturum anahtarını almak için bu komutu çalıştırın:

    curl -H "Content-Type: application/json" -d '{"id":1, "jsonrpc":"2.0", "method": "author_rotateKeys", "params":[]}' http://localhost:9944

   
    
  ###  6-Zenchain RPC'yi OKX cüzdanınıza ekleyin:
>-Ağ adı : Zenchain Testnet

>-RPC URL'si : https://zenchain-testnet.api.onfinality.io/public

>-Zincir Kimliği : 8408

>-SEMBOL : ZCX

>-Blok Gezgini : https://zentrace.io/

> ##### OKX Wallet kullanın, Zenchain Testnet ağına ayarlandığından emin olun. Inputa dikkat edin. sonuna eklenecek olanın başında 0x yok:

>-To :0x0000000000000000000000000000000000000802

>-Amount :0


>-Input Data: :

```
0xf1ec919c00000000000000000000000000000000000000000000000000000000000000200000000000000000000000000000000000000000000000000000000000000060 + oturum anahtarını yazın başında 0x olmadan yazın
```
<img width="283" alt="zen1" src="https://github.com/user-attachments/assets/ce69b5e7-5592-4fa4-875f-9ff5d2e71c28" />


### 7-Docker Durdurun ve Kaldırın:

```docker rm -f zenchain```

Artık oturum anahtarı bağlandığına göre, düğümü son kurulum komutuyla çalıştırın.

##### >YOURVALIDATORNAME kendiniz değiştirin 

```
docker run \
    -d \
    --name zenchain \
    -p 9944:9944 \
    -v "$HOME/chain-data:/chain-data" \
    ghcr.io/zenchain-protocol/zenchain-testnet:latest \
    ./usr/bin/zenchain-node \
    --base-path=/chain-data \
    --validator \
    --name="YOURVALIDATORNAME" \
    --bootnodes=/dns4/node-7242611732906999808-0.p2p.onfinality.io/tcp/26266/p2p/12D3KooWLAH3GejHmmchsvJpwDYkvacrBeAQbJrip5oZSymx5yrE \
    --chain=zenchain_testnet
```

### 8-Docker Günlüklerini Kontrol Edin 

```
docker logs -f zenchain
```

### 9-Şimdi Doğrulayıcı Panosuna gidin: https://node.zenchain.io/#/staking

Cick Stake > Click To Your Account > Click Become a Validator > Input any amount you want to stake > Click Start Staking and Done!

<img width="351" alt="zen2" src="https://github.com/user-attachments/assets/44cb27b5-e230-4294-8a0f-a9fa134e6780" />


<img width="413" alt="zen3" src="https://github.com/user-attachments/assets/67e03ada-0c0a-43cc-9e7d-866a4bc2110b" />


<img width="422" alt="zen4" src="https://github.com/user-attachments/assets/18cfe282-867a-4fa8-8cf7-26a5e66a3f5d" />

### 10- Düğüm Durumunu Doğrula:

Yaklaşık 1-2 saat sonra staking panosu üzerinden node’unuzun Zenchain doğrulayıcı listesinde görünür olup olmadığını kontrol edin.

# Beğenmeyi unutmayın lütfen
