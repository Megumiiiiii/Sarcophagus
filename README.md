<div id="header" align="center">
  <img src="https://media.giphy.com/media/aXE4aGVPDs1pGcm0y4/giphy.gif" height="338" width="600"/>
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

## Open port
```
sudo ufw allow 443/tcp; sudo ufw allow 80/tcp; sudo ufw enable
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

### Lalu masukan nominal ( Digging Fee 1 - 5 Free Bond lebih dari 100 )
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/215102620-1ed14a2c-8f11-4d1d-b7d4-e80aecfec100.png"</p>

### Setelah selesai Register

#### Jalankan Node nya
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
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/215103568-73db76de-ec4f-484e-9325-fc8a23ffb9d2.png"</p>
	

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

- Update Archaeologist dengan deposit 1 Sacro
```
docker compose exec -it archaeologist sh
cli update -f 1
```
```
exit
```

- Lalu Restart
```
COMPOSE_PROFILES=service docker compose stop
COMPOSE_PROFILES=service docker compose up -d
```


## CLI ( Command Line Interface )
#### Update Digging Fee ke 5
```
docker compose exec -it archaeologist sh
cli update -d 5
```
```
exit
```
5 bisa diubah berapapun

#### Menambah Free Bond 100
```
docker compose exec -it archaeologist sh
cli update -f 100
```
```
exit
```
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214585483-bd61c8a2-a6bc-41b5-b24f-fe73dd4cf41b.png"</p>
	
100 bisa diubah

#### Cek Profil
```
docker compose exec -it archaeologist sh
cli view -p
```
```
exit
```

#### Klaim Rewards
```
docker compose exec -it archaeologist sh
cli claim
```
```
exit
```

#### Withdraw 10 dari Free Bond
```
docker compose exec -it archaeologist sh
cli free-bond -w 10
```
```
exit
```
	
### Cek Domain
Masukan domain name kalian kesini https://www.nslookup.io/website-to-ip-lookup . Jika sudah sama dengan IP VPS berarti benar



## Daftar Peserta
- https://sarcopahgus.notion.site/Archaeologist-Testnet-Participant-Roster-e19dedd7d00346b2a20dce3aa46ab68b
- https://dev-sarcophagus.netlify.app/archaeologists
