<div align="center">
 
# Sarcophagus

</div>

<div align="center">

[![](https://img.shields.io/static/v1?label=Sponsor&message=%E2%9D%A4&logo=GitHub&color=%23fe8e86)](https://github.com/sponsors/Megumiiiiii)

 <img align="top" src="https://komarev.com/ghpvc/?username=Megumiiiiii&color=ff69b4&style=plastic&label=Visitors" height='35'/>

</div>

#

<div align="center">
  
## ${\color{blue} NGESHARE \space DI \space CHANNEL, \space APA \space COPAS \space SERTAIN \space SUMBER \space SU}$

### ${\color{cyan} DIKIRA \space BIKIN \space GINIAN \space GAK \space PERLU \space USAHA \space APA}$ 

</div>



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
```bash
  sudo apt update; sudo apt upgrade
```
```bash
sudo apt-get update && sudo apt install jq git && sudo apt install apt-transport-https ca-certificates curl software-properties-common -y && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add - && sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin && sudo apt-get install docker-compose-plugin
```

## Open port
```bash
sudo ufw allow ssh; sudo ufw allow 443/tcp; sudo ufw allow 80/tcp; sudo ufw enable
```

## Clone Repo
```bash
git clone https://github.com/sarcophagus-org/quickstart-archaeologist
cd quickstart-archaeologist
```
	
## Mulai
### Membuat file `.env`
```bash
cp .env.example .env
```

### Generate Mnemonic Pharse
```bash
COMPOSE_PROFILES=seed docker compose run seed-gen
```
*BACKUP*

#### Atau lanjut menggunakan pharse dari testnet

### Membuat blank file peer ID

```bash
touch peer-id.json
```

Jika masih ada peer-ID dari testnet, hapus dulu

```bash
rm peer-id.json
```


### Edit file .env
```bash
nano .env
```
Isi dengan data kalian
<p align="center"><img height="auto" height="auto" src="https://user-images.githubusercontent.com/98658943/214577366-9b373fe5-d2c5-4d78-b86e-9038a2dea585.png"</p>

Untuk mendapatkan Private Key, kalian bisa import Mnemonic nya ke Metamask, lalu lihat PrivKey dari sana. Dan untuk RPC Provider bisa dari Alchemy, silhakan buat APP Mainnet dan ambil RPC URL nya.
<p align="center"><img height="auto" height="auto" src="https://github.com/Megumiiiiii/Sarcophagus/assets/98658943/0e9ac62c-9bf2-4b38-a3bb-5296085fa98c"</p>


## Token Sacro
- Untuk mendapatkan Token bisa swap di Uniswap
- Pergi ke https://app.uniswap.org/
- Atau reward dari testnet, 1000 SARCO cukup
- SC Sarco: `0x7697B462A7c4Ff5F8b55BDBC2F4076c2aF9cF51A`

## Register
```
COMPOSE_PROFILES=register docker compose run register
```
Y, Enter

### Lalu masukan nominal ( DiggingFee 100 - 500, CurseFee 300, dan FreeBond  1000 )
<p align="center"><img height="auto" height="auto" src="https://github.com/Megumiiiiii/Sarcophagus/assets/98658943/cce8c4a4-3515-4861-8329-8ea0a451e699"</p>



## Setelah selesai Register

#### Jalankan Node nya
```
COMPOSE_PROFILES=service docker compose up -d
```

# SUDAH

## Command 

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
#### Update Digging Fee ke 300
```
docker compose exec -it archaeologist sh
cli update -d 300
```
```
exit
```
300 bisa diubah berapapun

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

