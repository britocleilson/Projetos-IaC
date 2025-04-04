
# Instalação e Configuração do Vagrant

## Windows 11

### Requisitos do Sistema

- Processador compatível com virtualização
- Memória RAM suficiente (recomendado mínimo de 4GB)
- Espaço em disco disponível


### Passo a Passo para Windows

1. **Instale o VirtualBox**
    - Baixe o VirtualBox e o Extension Pack correspondente do site oficial: https://www.virtualbox.org/wiki/Downloads
    - Execute o instalador do VirtualBox com as configurações padrão
    - Adicione o Extension Pack ao VirtualBox (Arquivo -> Preferências -> Extensões)[^1][^2]
2. **Instale o Git**
    - Baixe o Git do site oficial
    - Execute o instalador com as configurações padrão[^2]
3. **Instale o Vagrant**
    - Baixe o Vagrant do site oficial: https://releases.hashicorp.com/vagrant/
    - Execute o instalador com as configurações padrão
    - Reinicie o Windows[^2]
4. **Instale os Plugins do Vagrant**
    - Abra o Git Bash ou PowerShell
    - Execute os comandos:

```
vagrant plugin install vagrant-winnfsd
vagrant plugin install vagrant-vbguest
```

5. **Verifique a Instalação**
    - Abra o terminal e execute:

```
vagrant --version
```

    - Você deverá ver a versão do Vagrant instalada[^1]

## Debian 11

### Passo a Passo para Debian

1. **Instale o VirtualBox**

```
sudo apt-get install virtualbox
```

2. **Atualize os Pacotes do Sistema**

```
sudo apt update
```

3. **Instale o Vagrant**
    - Baixe a versão mais recente do Vagrant:

```
curl -O https://releases.hashicorp.com/vagrant/2.2.19/vagrant_2.2.19_x86_64.deb
```

    - Instale o pacote:

```
sudo apt install ./vagrant_2.2.19_x86_64.deb
```

    - Alternativamente, você pode instalar diretamente dos repositórios:

```
sudo apt -y install vagrant-libvirt
```

(Para usar com libvirt, adicione usuários ao grupo libvirt):

```
sudo usermod -aG libvirt seu_usuario
```

4. **Verifique a Instalação**

```
vagrant --version
```


## Rocky Linux 9

### Passo a Passo para Rocky Linux

1. **Atualize o Sistema**

```
sudo dnf check-update
sudo dnf update
sudo dnf install dnf-plugins-core
```

2. **Adicione o Repositório HashiCorp**

```
sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/RHEL/hashicorp.repo
sudo rpm --import https://rpm.releases.hashicorp.com/gpg
```

3. **Instale o Vagrant**

```
sudo dnf install vagrant
```

4. **Para usar com KVM (opcional)**
    - Habilite os repositórios necessários:

```
sudo dnf install epel-release
sudo dnf config-manager --set-enabled crb
```

    - Instale as ferramentas de desenvolvimento:

```
sudo dnf install gcc make perl kernel-devel kernel-headers bzip2 dkms elfutils-libelf-devel
sudo yum groupinstall "Development Tools"
sudo dnf install libvirt-devel
```

    - Instale o plugin do Vagrant para libvirt:

```
vagrant plugin install vagrant-libvirt
```

5. **Verifique a Instalação**

```
vagrant --version
```


## Uso Básico do Vagrant

1. **Crie um Diretório para seu Projeto**

```
mkdir ~/vagrant-project
cd ~/vagrant-project
```

2. **Inicialize um Vagrantfile**

```
vagrant init ubuntu/trusty64
```

(Substitua "ubuntu/trusty64" pela box que desejar)[^5][^7]
3. **Inicie a Máquina Virtual**

```
vagrant up
```

4. **Conecte-se à Máquina Virtual**

```
vagrant ssh
```

5. **Desligue a Máquina Virtual**

```
vagrant halt
```

6. **Destrua a Máquina Virtual (quando não for mais necessária)**

```
vagrant destroy
```


Estes passos fornecem uma configuração básica do Vagrant em diferentes sistemas operacionais. Você pode personalizar o Vagrantfile conforme suas necessidades específicas para configurar recursos como memória, CPU, redes e pastas compartilhadas.

<div>⁂</div>

[^1]: https://ipv6.rs/tutorial/Windows_11/Vagrant/

[^2]: https://github.com/neikei/install-vagrant-on-windows

[^3]: https://gist.github.com/jansanchez/10146556

[^4]: https://www.server-world.info/en/note?os=Debian_11\&p=vagrant\&f=1

[^5]: https://orcacore.com/install-and-use-vagrant-on-debian-11/

[^6]: https://idroot.us/install-vagrant-rocky-linux-9/

[^7]: https://computingforgeeks.com/using-vagrant-with-virtualbox-kvm-on-rocky/

[^8]: https://developer.hashicorp.com/vagrant/tutorials/get-started/install

[^9]: https://github.com/stemar/vagrant-rockylinux-9

[^10]: https://developer.hashicorp.com/vagrant/docs/installation

[^11]: https://www.youtube.com/watch?v=bzayQVYFqgA

[^12]: https://www.vagrantup.com

[^13]: https://studwww.itu.dk/~ropf/blog/vagrant_install.html

[^14]: https://superuser.com/questions/1769582/vagrant-virtualbox-on-debian-bullseye

[^15]: https://bizanosa.com/ubuntu-debian-install-libvert-for-vagrant/

[^16]: https://echowings.github.io/p/how-to-install-vagrant-on-debian-11/

[^17]: https://forum.cardano.org/t/vagrant-virtualbox-not-working-on-debian-11/107838

[^18]: https://wiki.debian.org/Vagrant

[^19]: https://cs-uob.github.io/COMS10012/exercises/part1/posix1/install.html

[^20]: https://portal.cloud.hashicorp.com/vagrant/discover/rockylinux/9

[^21]: https://github.com/rocky-linux/vagrant-anaconda

[^22]: https://forums.rockylinux.org/t/issue-downloading-rocky-linux-9-vagrant-box/16627

[^23]: https://infotechys.com/install-vagrant-on-rhel9/

[^24]: https://github.com/jnyryan/vagrant-windows10

[^25]: https://www.itu.dk/~ropf/blog/vagrant_install.html

[^26]: https://dev.to/sannae/setting-up-windows-virtual-test-environments-with-vagrant-4k1b

[^27]: https://www.youtube.com/watch?v=7DLfOGt8YvA

[^28]: https://www.youtube.com/watch?v=zHgUQnYpo_g

[^29]: https://linuxize.com/post/how-to-install-vagrant-on-debian-10/

[^30]: https://github.com/stemar/vagrant-debian-11

[^31]: https://www.ubuntumint.com/install-vagrant-in-linux/

[^32]: https://www.hostzealot.com/blog/how-to/utilizing-vagrant-with-virtualbox-on-debian-12

[^33]: https://developer.hashicorp.com/vagrant/install

[^34]: https://orcacore.com/install-vagrant-rocky-linux-8/

[^35]: https://github.com/VEuPathDB/vagrant-rocky9-webserver

[^36]: https://warewulf.org/docs/v4.5.x/contributing/development-environment-vagrant.html

