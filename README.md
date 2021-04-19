# Frontier Gentx

### Get Updates:
```
sudo apt-get update
sudo apt-get install build-essential -y
sudo apt-get install cmake gcc -y
```

### Export files:
```
wget https://golang.org/dl/go1.15.8.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.15.8.linux-amd64.tar.gz

echo 'export PATH="$PATH:/usr/local/go/bin"' >> ~/.bashrc
echo 'export GOPATH="$HOME/go"' >> ~/.bashrc
echo 'export PATH="$PATH:$GOPATH/bin"' >> ~/.bashrc
source ~/.bashrc
```

### Make sure go version installed in your system meets the minimum requirement of 1.15+
```
go version
```

### Installation
```
git clone https://github.com/frontierdotxyz/frontier-chain.git
cd frontier-chain && git checkout v0.1.0 && make install

frontd init XXXXXXXXXXXX --chain-id frontier-chain-testnet-0-black-mamba
frontcli config keyring-backend test
frontcli keys add XXXXXXXXXXXX
frontd add-genesis-account $(frontcli keys show XXXXXXXXXXXX -a) 1000000000000front
frontd gentx --name XXXXXXXXXXXX --amount 1000000000000front --keyring-backend test
```

### Send Gentx to GitHub
```
cd ~
git clone https://github.com/XXXXXXXXXXXX/frontier-chain-testnets

cd frontier-chain-testnets
cp ~/.frontd/config/gentx/gentx-XXXXXXXXXXXX.json ./0-black-mamba/gentx/gentx-XXXXXXXXXXXX.json

sudo git add .
sudo git commit -am "gentx-XXXXXXXXXXXX.json"
sudo git push origin
<github_username>
<github_password>
```
