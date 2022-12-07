# Inery-Taks-1
Tutorial Inery Master Node

## Minimal Spesifikasi
Rekomendasi Provider/ISP Hetzner CX51

|  Komponen |  Persyaratan Minimum |
| ------------ | ------------ |
| CPU  | 8 VCPU  |
| RAM | 16 GB  |
| Penyimpanan  | 240 GB |
| koneksi | Port 1 Gbit/dtk |
| OS | Ubuntu 20.04 |

### Update dan Install Tools

```
sudo apt-get update && sudo apt install git && sudo apt install screen
```

```
sudo apt-get install -y make bzip2 automake libbz2-dev libssl-dev doxygen graphviz libgmp3-dev \
autotools-dev libicu-dev python2.7 python2.7-dev python3 python3-dev \
autoconf libtool curl zlib1g-dev sudo ruby libusb-1.0-0-dev \
libcurl4-gnutls-dev pkg-config patch llvm-7-dev clang-7 vim-common jq libncurses5
```

### Open Port 

```
ufw allow 22 && ufw allow 8888 && ufw allow 9010 && ufw enable
```

### Download File Inery

```
git clone https://github.com/inery-blockchain/inery-node
```

### Berikan Izin

```
cd inery-node/inery.setup
chmod +x ine.py
./ine.py --export
cd; source .bashrc; cd -
```
### Edit Konfigurasi Master Node

Isi bagian Master Node masukkan nama akun, Publik Key, Private key, dan IP VPS
```
cd $home && cd inery-node/inery.setup/tools
nano config.json
```

### Start Node

```
screen -S inery
cd $home && cd inery-node/inery.setup
./ine.py --master
```
CTRL+A+D
```
cd $home
cd ~/inery-node/inery.setup/master.node
chmod +x start.sh
./start.sh
```

### Cek Log

```
tail -f $HOME/inery-node/inery.setup/master.node/blockchain/nodine.log
```
Tunggu Hingga Sync jika sudah Sync buat wallet

### Buat Wallet

```
cline wallet create -n (nama walletmu) -f file.txt
```
Masukkan Private key 

```
cline wallet import --private-key (private keymu) -n (nama walletmu)
```
File Private Key akan tersimpan di root file.txt (Untuk membuka wallet jika terkunci)

### Daftar agar menjadi produser block Inery

```
cline system regproducer (nama akunmu) (publik keymu) 0.0.0.0:9010
```
```
cline system makeprod approve (nama akunmu) (nama akunmu)
```

### Cara membuka Wallet jika terkunci

```
cline wallet unlock -n (nama walletmu)
```

# Terima Kasih Banyak (Thank You Very Much)
