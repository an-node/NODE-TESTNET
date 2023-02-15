<p align="center">
  <img height="50" height="auto" src="https://user-images.githubusercontent.com/38981255/184088981-3f7376ae-7039-4915-98f5-16c3637ccea3.PNG">
</p>

# Install Become a Master Node

> [DOCS](https://docs.inery.io/docs)
> 
> [Explorer Inary](https://explorer.inery.io/ "Explorer Inary")

## Minimum Spec Hardware :
NODE  | CPU     | RAM      | SSD     | OS     |
| ------------- | ------------- | ------------- | -------- | -------- |
| Inery | 4          | 8         | 50  | Ubuntu 20.04 LTS  |


## Update Inery-node

* Stop Node
  ```console
  cd $HOME/inery-node/inery.setup/master.node
  ./stop.sh
  ```
  Check 
  ```console
  pidof nodine
  ```
    Execute Stop 
  ```console
  pidof -9 <pid>
  ```

* Delete Folder Inery node
  ```console
  cd $HOME
  rm -rf inery-node
  ```

* Download Inery node
  ```console
   git clone  https://github.com/inery-blockchain/inery-node
  ```

* Goto Folder `inery.setup`
  ```console
   cd inery-node/inery.setup
  ```

* executable `ine.py`
  ```console
  chmod +x ine.py
  ```

* Export path
  ```console
  ./ine.py --export
  ```

* Load path
  ```console
  source $HOME/.bashrc
  ```

* Config Edit
  ```console
  nano tools/config.json
  ```
  Cari `MASTER_ACCOUNT` lalu ubah value seperti berikut
  | Variable | Data |
  |-----------|------------|
  |NAME|Inery Account|
  |PUBLIC_KEY|Public Account|
  |PRIVATE_KEY|Privaet Account|
  |PEER_ADDRESS|127.0.0.1:9010|

 Save <kbd>CTRL</kbd>+<kbd>x</kbd>+<kbd>y</kbd>

* Run node
  ```console
  ./ine.py --master
  ```

* Check log node
  ```console
  tail -f master.node/blockchain/nodine.log
  ```

If it's syncron run`start.sh`
```console
./master.node/start.sh
```

## Troubleshoot

Erorr : FileNotFoundError: [Errno 2] No such file or directory: './blockchain/config/config.ini'

Indication :  `libssl 1.1` not installed properly

Solution : 
```
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb
```

### net_plugin::plugin_startup failed to bind to port 9010

Jika pesan error ini muncul maka penyebabnya karena `nodine` masinh berjalan di latar belakang, solusinya adalah mematikan `nodine`. Anda bisa menggunakan perintah dibawah untuk mematikan `nodine`

```
pidof nodine

pidkill -9 <pid>
```

Untuk memastikan bahwa `nodine` sudah berhenti, anda bisa menggunakan perintah ini

```
pidof nodine
```

Setelah memastikan `nodine` benar-benar berhenti, anda dapat menjalankan node lagi