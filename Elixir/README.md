
![3](https://user-images.githubusercontent.com/96678356/218298522-286483f5-7a46-4d86-a877-48ceba240395.JPG)


# Install Validator Elixir Protocol

[WEBSITE](https://elixir.finance/)

[DOCS](https://docs.elixir.finance/)

[EXPLORER](https://metrics.elixir.finance/)

[DISCORD](https://discord.gg/Zxu9xhEN)

### Minimum Spec Hardware :
NODE  | CPU     | RAM      | SSD     | OS     |
| ------------- | ------------- | ------------- | -------- | -------- |
| ELixir | 2          | 4         | 50  | Ubuntu 20.04 LTS  |

### Open Port
```
apt install ufw -y
ufw allow ssh
ufw allow https
ufw allow http
ufw allow 17684
ufw enable
```
### Install Docker [Skip if previously installed docker on a different node]
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
$(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update && sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y </dev/null && sudo chmod 666 /var/run/docker.sock
```
### Create New Wallet EVM

### Download Dockerfile
```
wget https://testnet-1-files.elixir.finance/Dockerfile
```
### Edit Dockerfile
```
nano Dockerfile
```
### Input Wallet & PrivateKey

### Save Ctrl X + y

### Build Screen 
```
apt install screen -y
```
### Add Screen 
```
screen -R elixir
```
### Build docker
```
docker build . -f Dockerfile -t elixir-validator
```
### Update docker
```
docker kill ev
docker rm ev
docker pull elixirprotocol/validator:testnet-1
docker build . -f Dockerfile -t elixir-validator
```
### RUN 
```
docker run -d --restart unless-stopped --name ev elixir-validator
```
### Check logs
```
docker logs -f ev
```
### Register Wallet to [DISCORD](https://discord.gg/Zxu9xhEN)
![1](https://user-images.githubusercontent.com/96678356/218298328-2d190c0f-5332-403f-9b65-7617d22b160c.jpg)

### Suceesss Register
![2](https://user-images.githubusercontent.com/96678356/218298346-cb84ea0c-62cf-4800-ae10-b0a3fc8d4d76.PNG)

### Check Wallet In [EXPLORER](https://metrics.elixir.finance/)
- CTRL F & CTRL V wallet
![4](https://user-images.githubusercontent.com/96678356/218298686-f56a58db-f597-4ec3-8e55-6e992c14f6cb.png)

### Try Aagin If VALID ORDER = 0 [EXPLORER](https://metrics.elixir.finance/)

#### Open screen
```
screen -Rd elixir
```
```
docker kill ev
docker rm ev
docker pull elixirprotocol/validator:testnet-1
docker build . -f Dockerfile -t elixir-validator
docker run -d --restart unless-stopped --name ev elixir-validator
docker logs -f ev
```
Active Screen 
```
CTRL a + d
```
