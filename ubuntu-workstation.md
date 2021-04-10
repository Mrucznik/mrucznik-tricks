# My ubuntu configuration


## Install packages

### Essentials

```sh
sudo apt install \
  curl \
  fish \
  terminator \ 
  net-tools \
  whois \
  htop \ 
  make \ 
  cmake \ 
  git-lfs
```


### Languages

#### [Golang](https://github.com/golang/go/wiki/Ubuntu) 

```sh
sudo apt install software-properties-common
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt update
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6BC817356A3D45E
sudo apt install golang-go
```

#### [Rust](https://www.rust-lang.org/tools/install)

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

#### [Python](https://www.python.org/)

```sh

```

#### [Node.js](https://github.com/nodesource/distributions)

```sh
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_15.x | sudo -E bash -
sudo apt-get install -y nodejs
```

#### [Deno](https://deno.land/)

```sh
# With rust installed previously
cargo install deno --locked

# or with snap
sudo snap install deno
```

#### [Julia](https://julialang.org/)

#### C# & .NET Core

```sh
# Add sources
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

# Install
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

#### [Java](https://www.java.com/en/download/)

```sh

```

### Tools

