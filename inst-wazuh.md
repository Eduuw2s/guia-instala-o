# Instalação do Wazuh no VirtualBox (Linux)

Este guia apresenta o passo a passo para instalar o Wazuh Server em uma máquina virtual Linux utilizando o VirtualBox.

---

## 1. Pré-requisitos

- Oracle VirtualBox instalado ([Download](https://www.virtualbox.org/))
- Imagem ISO de uma distribuição Linux suportada pelo Wazuh (exemplo: Ubuntu Server 22.04 LTS)
- Acesso à internet

---

## 2. Criando a Máquina Virtual

1. **Abra o VirtualBox e clique em “Novo”**
2. **Nomeie a VM** (ex: `Wazuh-Server`)  
   - **Tipo:** Linux  
   - **Versão:** Ubuntu (64-bit) ou conforme sua ISO
3. **Ajuste a Memória RAM**  
   - Recomenda-se pelo menos 4 GB (4096 MB)
4. **Crie um disco rígido virtual agora**  
   - Tipo: VDI  
   - Tamanho dinâmico  
   - Tamanho: 40 GB (ou conforme necessidade)

---

## 3. Configurando a Mídia de Instalação

1. **Selecione a VM recém-criada e clique em “Configurações”**
2. Vá em “Armazenamento” > “Controladora IDE” > clique no ícone de disco ao lado de “Vazio”
3. Escolha “Selecionar um arquivo de disco óptico virtual” e aponte para a ISO do Linux

---

## 4. Instalando o Sistema Operacional

1. Clique em “Iniciar” para ligar a VM
2. Instale o sistema operacional Linux normalmente (exemplo: Ubuntu Server)
3. Faça todos os updates após a instalação:
    ```sh
    sudo apt update && sudo apt upgrade -y
    ```

---

## 5. Instalando o Wazuh Server

> Exemplo para Ubuntu Server 22.04 LTS. Consulte sempre a [documentação oficial](https://documentation.wazuh.com/current/installation-guide/index.html) para outros sistemas.

1. **Baixe e execute o instalador do Wazuh:**
    ```sh
    curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh
    sudo bash ./wazuh-install.sh -a
    ```
    - O parâmetro `-a` instala o Wazuh Server completo (manager, dashboard e indexer).

2. **Aguarde a instalação ser concluída.**

3. **Acesse o painel web do Wazuh:**
    - Abra o navegador e acesse: `https://<IP-da-VM>:5601`
    - Usuário padrão: `admin`
    - Senha: exibida no final da instalação (ou use `sudo cat /var/ossec/api/configuration/auth/credentials.json`)

---

## 6. Observações

- Ajuste o firewall caso necessário para liberar acesso à porta 5601 (painel web).
- Consulte a documentação para adicionar agentes (como o Windows Server 2008).
- Para ambientes de produção, aumente recursos e segurança conforme necessário.
