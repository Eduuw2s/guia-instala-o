# Configuração de DHCP

## Como funciona o DHCP

O DHCP (Dynamic Host Configuration Protocol) automatiza a atribuição de IPs na rede.

---

## DHCP no Windows Server 2008

1. Abra o "Gerenciador de Servidores"
2. Clique em "Adicionar Funções" e selecione "Servidor DHCP"
3. Siga o assistente para configurar escopo, faixa de IP, gateway e DNS
4. Ative o serviço DHCP

---

## DHCP no Debian/Kali Linux

1. Instale o servidor DHCP:

   ```bash
   sudo apt update
   sudo apt install isc-dhcp-server
   ```

2. Edite o arquivo de configuração `/etc/dhcp/dhcpd.conf`:

   ```bash
   subnet 192.168.1.0 netmask 255.255.255.0 {
     range 192.168.1.100 192.168.1.200;
     option routers 192.168.1.1;
     option domain-name-servers 8.8.8.8, 8.8.4.4;
   }
   ```

3. Defina a interface de rede em `/etc/default/isc-dhcp-server`:

   ```
   INTERFACESv4="eth0"
   ```

4. Reinicie o serviço:

   ```bash
   sudo systemctl restart isc-dhcp-server
   ```

5. Verifique o status:

   ```bash
   sudo systemctl status isc-dhcp-server
   ```

---
