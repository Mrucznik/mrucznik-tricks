# My ubuntu configuration

I use [Ubuntu 21.04](https://ubuntu.com/blog/ubuntu-21-04-is-here)


## Install packages

### Essentials

```sh
sudo apt install \
  curl \
  net-tools \
  whois \
  htop \
  iotop \
  iftop \
  git-lfs \
  openvpn \
  gnome-tweaks
```


### Languages

#### [C/C++](https://www.cplusplus.com/)

```sh
sudo apt install gcc clang make cmake
```

#### [Golang](https://github.com/golang/go/wiki/Ubuntu) 

```sh
# By snap
sudo snap install go

# By apt on Ubuntu 21.04
sudo apt install software-properties-common
sudo add-apt-repository ppa:longsleep/golang-backports
sudo apt update
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6BC817356A3D45E
sudo apt install golang-go
```

[Yeagi](https://github.com/traefik/yaegi) interpreter
```sh
go get -u github.com/traefik/yaegi/cmd/yaegi
```

#### [Rust](https://www.rust-lang.org/tools/install)

```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

#### [Python](https://www.python.org/)

```sh
# Install python 2, python 3 & pip
sudo apt install python python3 python3-pip python3-virtualenv

# Set python 3 as default python
# Per user:
echo "alias python=python3" >> ~/.bash_aliases
source ~/.bash_aliases
# Or system wide:
update-alternatives --install /usr/bin/python python /usr/bin/python3 1
```

#### [Node.js](https://github.com/nodesource/distributions)

```sh
# Using Ubuntu
curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash -
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

```sh
# With jill (python & pip required) for current user

# Install jill
pip install jill --user -U
echo "export PATH=~/.local/bin:$PATH" >> ~/.bashrc
source ~/.bashrc

# Install julia
jill install 1.6.0
```

#### [C# & .NET Core](https://docs.microsoft.com/en-US/dotnet/core/install/linux-ubuntu#2010-)

```sh
# Add sources
wget https://packages.microsoft.com/config/ubuntu/21.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb

# Install
sudo apt-get update; \
  sudo apt-get install -y apt-transport-https && \
  sudo apt-get update && \
  sudo apt-get install -y dotnet-sdk-5.0
```

#### [Java](https://www.java.com/en/download/)

```sh
# Install openjdk
sudo apt install openjdk-15-jdk
```

### Tools

#### [Docker](https://docs.docker.com/)

```sh
# Set up the repository
sudo apt-get update
sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
    
# Add Docker’s official GPG key
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

# Add stable repository
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io

# Verify installation
sudo docker run hello-world

# Install additional toolings
sudo apt install docker-compose
```

#### [Podman](https://podman.io/)

```sh
# Ubuntu 20.10 and newer
sudo apt-get -y update
sudo apt-get -y install podman

# Verify installation
sudo podman run hello-world

# Install additional toolings
pip3 install podman-compose
```

#### [Jupyter-Notebook](https://jupyter.org/)

```sh
sudo apt install jupyter-notebook
```

[Also with golang](https://github.com/gopherdata/gophernotes)!
```sh
env GO111MODULE=on go get github.com/gopherdata/gophernotes
mkdir -p ~/.local/share/jupyter/kernels/gophernotes
cd ~/.local/share/jupyter/kernels/gophernotes
cp "$(go env GOPATH)"/pkg/mod/github.com/gopherdata/gophernotes@v0.7.3/kernel/*  "."
chmod +w ./kernel.json # in case copied kernel.json has no write permission
sed "s|gophernotes|$(go env GOPATH)/bin/gophernotes|" < kernel.json.in > kernel.json
```


### IDE's

#### [Visual Studio Code](https://code.visualstudio.com/)

```sh
sudo snap install code --classic
```

#### [Atom](https://atom.io/) with [Juno](https://junolab.org/) for Julia

```sh
sudo snap install atom --classic
```

In Atom, go to Settings (Ctrl+,, or Cmd+, on macOS. Note that this is Control plus comma!) and go to the "Install" panel.
Type uber-juno into the search box and hit enter. Click the install button on the package of the same name.

#### [JetBrains IDE's](https://www.jetbrains.com)

```sh
sudo snap install intellij-idea-ultimate --classic
sudo snap install pycharm-professional --classic
sudo snap install webstorm --classic
sudo snap install clion --classic
sudo snap install goland --classic
sudo snap install datagrip --classic
sudo snap install rider --classic
```

### Others

#### Firefox 

By default installed on ubuntu.

#### Brave

```sh
sudo snap install brave
```

#### Spotify

```sh
sudo snap install spotify
```

## Drivers

### Auto install drivers

```sh
sudo ubuntu-drivers autoinstall
```

### Install pipewire sound drivers

Follow the instructions from https://github.com/pipewire-debian/pipewire-debian#add-the-launchpad-ppa






