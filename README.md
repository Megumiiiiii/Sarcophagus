<div id="header" align="center">
  <img src="https://media.giphy.com/media/WSHTkvpcbd5Un2pklG/giphy.gif" height="338" width="600"/>
</div>

<h1 align="center">Sarcophagus</h1>

![image](https://user-images.githubusercontent.com/98658943/214569281-4d9d3e0e-f1c5-4933-8559-07576ef885d7.png)

## Minimum Spek
> 10GB SSD
> 1GB RAM

## Domain
Garapan ini perlu domain pribadi seperti .com .net .id etc. Kalian bisa beli di Namecheap, Niagahoster, Contabo, atau manapun terserah.

### Setelah beli
- Masuk ke kelola domain (disni menggunakan niagahoster)
- Tambahkan DNS Record
<p align="left"><img height="auto" width="auto" src="https://user-images.githubusercontent.com/98658943/214573355-e3f22b37-639c-4824-9024-11db2b05f96b.jpg"</p>
  
- Pilih *A*
<p align="left"><img height="auto" width="auto" src="https://user-images.githubusercontent.com/98658943/214574697-114cc2de-bb50-4ef0-885f-2bb0d6c37c8f.jpg"</p>
  
- Masukan nama dan IP VPS
<p align="left"><img height="auto" width="auto" src="https://user-images.githubusercontent.com/98658943/214574980-6d5b2864-a0e7-46c6-b6bf-66edf3e027bd.jpg"</p>
  
- Simpan
  
## Install segala keperluan
```
  sudo apt update; sudo apt upgrade
```
```
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```

## Clone Repo
```
git clone https://github.com/sarcophagus-org/quickstart-archaeologist
cd quickstart-archaeologist
```
	
## Mulai
### Membuat file `.env`
```
cp .env.example .env
```

### Generate Mnemonic Pharse
```
COMPOSE_PROFILES=seed docker compose run seed-gen
```
*BACKUP*

### Membuat blank file peer ID
```
touch peer-id.json
```

### Edit file .env
```
nano .env
```
Isi dengan data kalian
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214577366-9b373fe5-d2c5-4d78-b86e-9038a2dea585.png"</p>

Untuk mendapatkan Private Key, kalian bisa import Mnemonic nya ke Metamask, lalu lihat PrivKey dari sana. Dan untuk RPC Provider bisa dari Alchemy, silhakan buat APP Goerli dan ambil RPC URL nya.
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214587355-e545b4ff-8207-484b-aa5e-172aa0b52d9a.png"</p>



## Token Sacro
- Untuk mendapatkan Token bisa swap di Uniswap
- Kirim Goerli ke Wallet yang di generate tadi
- Pergi ke https://app.uniswap.org/ 
- Swap Goerli ke Sarco. SC Sarco: `0x4633b43990b41B57b3678c6F3Ac35bA75C3D8436`

## Register
```
COMPOSE_PROFILES=register docker compose run register
```
Y, Enter

### Lalu masukan nominal ( Kalau bisa 100 dan 100, lebih gpp )
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214579815-7a582490-62a1-44ba-a5f5-7ac551206eac.png"</p>

### Setelah selesai Register
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214580545-46e1c41f-1bba-4a95-8190-7e77b6be89d6.png"</p>

Jalankan Node nya
```
COMPOSE_PROFILES=service docker compose up -d
```

# SUDAH

## Command yang mungkin berguna

### Cek apakah node nya jalan pa ngga
```
docker container ls
```
Copy ID dari yang ada service2nya
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214582956-e20e6a96-9bd0-4cfc-9244-9b6a038bf882.png"</p>

Lalu
```
docker logs -f ContainerIDMu
```
Output yang benar
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214584736-bc77a5cb-7197-4c2e-ae1d-3072d654466a.png"</p>


### Jika ada update di waktu mendatang
```
cd ~/quickstart-archaeologist
COMPOSE_PROFILES=service docker compose stop
COMPOSE_PROFILES=service docker compose pull
COMPOSE_PROFILES=service docker compose up -d
```
### Restart Node
```
COMPOSE_PROFILES=service docker compose stop
COMPOSE_PROFILES=service docker compose up -d
```

### Jika mengubah domain setelah Resgister
```
- Update Archaeologist dengan deposit 1 Sacro
```
docker compose exec -it archaeologist sh
cli update -f 1
exit
```

- Lalu Restart
```
COMPOSE_PROFILES=service docker compose stop
COMPOSE_PROFILES=service docker compose up -d
```


## CLI ( Command Line Interface )
#### Update Digging ke 10
```
docker compose exec -it archaeologist sh
cli update -d 10
exit
```
10 bisa diubah berapapun

#### Menambah Free Bond ke 100
```
docker compose exec -it archaeologist sh
cli update -f 100
exit
```
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214585483-bd61c8a2-a6bc-41b5-b24f-fe73dd4cf41b.png"</p>
	
100 bisa diubah

#### Cek Profil
```
docker compose exec -it archaeologist sh
cli view -p
exit
```

#### Klaim Rewards
```
docker compose exec -it archaeologist sh
cli claim
exit
```

#### Withdraw 10 dari Free Bond
```
docker compose exec -it archaeologist sh
cli free-bond -w 10
exit
```




