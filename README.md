# Arquitetura de Infraestrutura Híbrida CANTU PNEUS
## Equipamentos utilizados On-Primese 
### Matriz-Escritório
- 1 Routerborder Mikrotik - LINK1
- 1 Routerborder Mikrotik - LINK2
- 1 Firewall de borda Fortigate - FW01
- 1 Firewall de borda Fortigate - FW02 
- 1 Switch L3 HP - SW-CORE01 
- 1 Switch L3 HP - SW-CORE02 
- 1 Switch L3 HP - SW-DIST01
- 1 Switch L3 HP - SW-DIST02
- 1 Switch L2 HP - SW-ACCE01
- 1 Switch L2 HP - SW-ACCE02
- 1 Server Dell - SRV-HOST01
- 1 Server Dell - SRV-HOST02
- 6 Access Point Unifi - AP-01/6

### Matriz-Armazém
- 1 Switch L3 HP - SW-DIST03
- 1 Switch L3 HP - SW-ACCE03
- 8 Acess Point Unifi - AP-07/14

# Configuração dos Dispostivos de Rede 
## Switches Core
### Configuração Global  
- Configurado interfaces trunk\Access
- Configurado SNMP
- Configurado name
- Configurado clock
- Configurado acesso
- Configurado ACLs
- Configurado endereço IP
- Configurado o empilhamento dos switches
- Configurado rota default

### Criado VLANs e configurado sub-redes
- VLAN4 (Trânsito) - 172.16.4.1/22
- VLAN6 (Trânsito) - 172.16.6.1/22
- VLAN10 (Gerência) - 172.16.1.254/22
- VLAN30 (WIFI) - 172.16.3.254/22
- VLAN50 (Usuários) - 172.16.5.254/22
- VLAN100 (Servidores) - 172.16.0.254/22
- VLAN300 (LINK1)
- VLAN400 (LINK2)

### Configuração do Spanning Tree
- Habilitado o Spanning Tree mode RSTP 
- Configurado prioridade root bridge
- Configurado loopback-guard

## Switches de Distribuição
### Configuração Global
- Configurado interfaces trunk\Access
- Configurado SNMP
- Configurado name
- Configurado clock
- Configurado acesso
- Configurado ACLs
- Configurado endereço IP
- Configurado rota default

### Criado VLANs
- VLAN10 (Gerência)
- VLAN30 (WIFI)
- VLAN50 (Usuários)
- VLAN100 (Servidores)
- VLAN300 (LINK1)
- VLAN400 (LINK2)

### Configuração do Spanning Tree
- Habilitado o Spanning Tree mode RSTP 
- Configurado prioridade root bridge
- Configurado loopback-guard

## Firewalls Fortigate
- Configurado o HA - alta disponilibilidade
- Realizado integração com o AD
- Criado as vlans de trânsito e demais
- Criado Roteamento 
- Configurado os VIP
- Configurado os Gateways
- Configurado WebFilter
- Configurado Firewall Policy
- Configurado SDWAN;
- Configurado SSL VPN
- Liberado portas e URLS para o AD Connect

## Servidores Dell
- Criado RAID10  
- Instalado e configurado o Hyper-V Server
- Criado as máquina virtuais: VSRV-AD01, VSRV-AD02, VSRV-AADC, VSRV-FS01, VSRV-FS02, VSRV-DEV, VSRV-PRNT e VSRV-UNIF
- VM VSRV-AD01: Instalado Windows Server 2022. Instalado Active Directory Domain Services (AD DS) e promovido a controlador de domínio. Configurado UPN com sufixo cantupneus.com.br. Configurado OU, grupos e usuários. Instalado e configurado o serviço de NPS para 802.1x Wireless
- VM VSRV-AD02: Instalado Windows Server 2022. Instalado e configurado o controlador de domínio secundário e validado a replicação
- VM VSRV-AADC: Instalado Windows Server 2022. Ingressado no domínio, instalado e configurado o AAD Connect
- VM VSRV-FS01: Instalado Windows Server 2022. Instalado a função de file server. Instalado e configurando o DFS e replicação de arquivos
- VM VSRV-FS02:Instalado Windows Server 2022. Instalado e configurando o DFS e replicação de arquivos
- VSRV-DEV: Instalado Windows Server 2022. Instalado e configurado o  Git, GitHub, MYSQL, MYSQL Workbench, Dotnet8 e Nodejs e demais dependências
- VSRV-PRNT: Instalado Windows Server 2022. Instalado e configurado o PrintServer 
- VSRV-UNIF: Instalado Linux Debian. Instalado e configurado o controller Unifi. Criado Radius profile. 


# Cloud Microsoft Azure
## Azure Active Directory
- Criado conta Azure
- Criado Tenant
- Adicionado domínio da empresa
- Criado usuário global administrator
- Habilitado o MFA
- Criado e configurado o Registro da aplicação para SSO (Single Sign-On)

## Serviços de Aplicativos
- Integrado o aplicativo com o GitHub 
- Integrado o aplicativo com o banco de dados
- Habilitado e configurado os logs de diagnóstico
- Configurado domínios personalizados
- Configurada uma regra de firewall para permitir o acesso ao backoffice a partir do intervalo de IPs públicos no on-premise

## WebApp Backend
- Criado o aplicativo Web
- Criado um grupo de recurso
- Ambiente Linux
- Definido o plano de serviço de aplicativo (Produção)
- Configurado Backup
- Habilitado o auto scale automático
- Definido framework dotnet8

## WebApp Frontend
- Criado o aplicativo Web
- Criado um Grupo de recurso
- Ambiente Linux
- Definido o plano de serviço de aplicativo (Produção)
- Configurado Backup
- Habilitado o auto scale automático
- Definido a ferramenta nodejs

## Banco de dados MYSQL
- Criado servidor de banco de dados
- Defino grupos de recurso
- Definido as credenciais 
- Definido a localização
- Definido a versão
- Definido o Hardware

## Azure Front Door
- Criado Front Door 
- Configurado roteamento
- Configurado WAF (Regras de proteção, DDoS, Listas de permissões/Negações) 






