- **[PT](#documentação-da-instalação-e-configuração-do-tailscale-em-sistemas-linux)**
- **[EN](#tailscale-installation-and-configuration-documentation-for-linux-systems)**

------
------

# Documentação da Instalação e Configuração do TailScale em Sistemas Linux

Tailscale é uma solução de VPN mesh baseada no WireGuard, que simplifica a ligação segura de dispositivos e serviços em diferentes redes.

Ao contrário de VPNs tradicionais, o Tailscale não exige a configuração de um servidor VPN com um endereço público para permitir a conexão dos clientes.

A seguinte documentação descreve o processo de instalação e configuração do serviço TailScale em sistemas operativos baseados em Linux, permitindo a criação de uma rede privada partilhada entre vários utilizadores.

## Pré-requisitos

Antes de prosseguir com a instalação do TailScale, e necessário aceder ao site oficial [1](#bibliografia) do TailScale e criar uma conta.

## Instalação

Por forma a instalar o TailScale, execute os seguintes passos.

**1. Atualização do Sistema Operativo**:

```bash
sudo apt update
sudo apt upgrade
```

**2. Adicionar o Repositório**:

Execute os seguintes comandos para adicionar o repositório do TailScale ao sistema.

+ **Ubuntu 24**

    ```bash
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/noble.noarmor.gpg | sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/noble.tailscale-keyring.list | sudo tee /etc/apt/sources.list.d/tailscale.list
    ```

+ **Debian 12**

    ```bash
    curl -fsSL https://pkgs.tailscale.com/stable/debian/bookworm.noarmor.gpg | sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null
    curl -fsSL https://pkgs.tailscale.com/stable/debian/bookworm.tailscale-keyring.list | sudo tee /etc/apt/sources.list.d/tailscale.list
    ```

No caso do sistema operativo ser diferente de `Debian` ou `Ubuntu`, consulte a documentação oficial [2](#bibliografia).

**3. Instalar o TailScale**:
   
```bash
sudo apt update
sudo apt install tailscale
```

## Configuração

Siga os seguintes passos para iniciar e configurar o TailScale.

**1. Login**:

Antes de começar a configuração do TailScale é necessário realizar Login através do Link que aparece no terminal ao executar o seguinte comando:

```bash
sudo tailscale up
```

Feito o login, execute o seguinte comando para verificar o estado da conexão do TailScale.

```bash
sudo tailscale status
```

**2. Adicionar Utilizadores à Rede do TailScale**:

Acedendo ao Painel de Controlo do TailScale, navegue até à página "Users". Clique em "Invite external users", adicione o email do utilizador e as devidas permissões.

O utilizador convidado irá receber um e-mail com o link para aceder à Rede do TailScale. Para isso o convidado terá de criar conta e aceder à rede criada pelo dispositivo principal.

**4. Testar a Conexão**:

Se tudo estiver bem configurado na página "Users" irá ver todos os dispositivos da Rede. Para testar a conexão entre os dispositivos execute o seguinte comando:

```bash
sudo tailscale ping <IP/hostname>
```

## Bibliografia

- [1 - Site Oficial](https://tailscale.com/)
- [2 - Documentação Oficial do TailScale](https://tailscale.com/download/linux)

------
------

# TailScale Installation and Configuration Documentation for Linux Systems

Tailscale is a WireGuard-based mesh VPN solution that simplifies the secure connection of devices and services across different networks.

Unlike traditional VPNs, Tailscale does not require you to configure a VPN server with a public address to allow clients to connect.

The following documentation describes the process of installing and configuring TailScale on Linux-based operating systems, allowing the creation of a private network shared between multiple users.

## Prerequisites

Before proceeding with the installation of TailScale, access the official TailScale website [1](#bibliography) and create an account.

## Installation

In order to install TailScale, perform the following steps.

**1. Update the Operating System**:

```bash
sudo apt update sudo apt upgrade
```

**2. Add the Repository**:

Run the following commands to add the TailScale repository to the system.

+ **Ubuntu 24**

    ```bash
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/noble.noarmor.gpg | sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null
    curl -fsSL https://pkgs.tailscale.com/stable/ubuntu/noble.tailscale-keyring.list | sudo tee /etc/apt/sources.list.d/tailscale.list
    ```

+ **Debian 12**

    ```bash
    curl -fsSL https://pkgs.tailscale.com/stable/debian/bookworm.noarmor.gpg | sudo tee /usr/share/keyrings/tailscale-archive-keyring.gpg >/dev/null
    curl -fsSL https://pkgs.tailscale.com/stable/debian/bookworm.tailscale-keyring.list | sudo tee /etc/apt/sources.list.d/tailscale.list
    ```

If the operating system is different from `Debian` or `Ubuntu`, consult the official documentation [2](#bibliography).

**3. Installing TailScale**: 

```bash
sudo apt update sudo apt install tailscale
```

## Configuration

Follow the steps below to start and configure TailScale.

**1. Login**:

Before starting the Tailscale configuration, it's required to log in using the provided link, generated by executing the following command:

```bash
sudo tailscale up
```

Once logged in, execute the following command to check the status of the TailScale connection.

```bash
sudo tailscale status
```

**2. Adding Users to the TailScale Network**:

Access the TailScale Control Panel and navigate to the "Users" page. Click on "Invite external users", and add the user's email and the appropriate permissions.

The invited user will receive an email with a link to access the TailScale Network. To do this, the guest will have to create an account and access the network created by the main device.

**4. Testing the Connection**:

If everything is configured correctly on the "Users" all the devices on the Network will be displayed. To test the connection between the devices, execute the following command:

```bash
sudo tailscale ping <IP/hostname>
```

## Bibliography

- [1 - Official Site](https://tailscale.com/)
- [2 - TailScale Official Documentation](https://tailscale.com/download/linux)