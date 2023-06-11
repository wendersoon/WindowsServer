# Servidor DNS

<div align="center">

<img src = https://github.com/wendersoon/WindowsServer/assets/104470835/1a913f46-9113-4502-9a42-734f9ec36bf1 width="500" />

</div>

  
Para começarmos precisamos enteder o **DNS** (Domain Name System) que é um sistema de nomenclatura de domínios que atribui nomes **amigáveis e fáceis** de lembrar a endereços IP numéricos, que são usados para identificar servidores e dispositivos na internet. Em vez de digitar uma sequência de números para acessar um site ou serviço, o DNS permite que os usuários simplesmente digitem um nome de domínio, como "google.com", e o sistema se encarrega de traduzir esse nome em um endereço IP correspondente. Imagina se toda que você precisasse acessar um site tivesse de lembrar o IP dele, atualmente isso é impossível e ainda bem que há o serviço DNS. Para saber mais veja esse [artigo](https://www.cloudflare.com/pt-br/learning/dns/what-is-dns/) da Cloudflare que oferece um dos maiores serviços de DNS do mundo.<br>

Neste artigo instalaremos e faremos a configuração do nosso servidor DNS.

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele(ou se quiser, apenas a parte da instalação), pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.***

## Instalação

Para instalar acesse seu Server Manager e vá na guia `Manage -> Add Rules and Features`, procure pelo serviço *DNS Server* como no print abaixo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ba33f57a-1ce8-4422-8e70-619ac6f5dc1a)

Não esqueça de salvar as configurações na sua pasta. Termine a instalação.

## Configuração

1. Nas configurações de rede do servidor faça a seguinte configuração(lembre-se que configuramos inicialmente no segundo artigo dessa sequência):

![Screencast from 11-06-2023 11_00_45](https://github.com/wendersoon/WindowsServer/assets/104470835/65b89385-9199-4ac3-8729-07a901f47878)

É interessante adicionar o sufixo do DNS com o mesmo nome que você colocou como domínio no Active Directory. 


1. No Server Manager acesse a guia `Tools` e procure por DNS:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2cea6881-c115-45d3-88e6-5867c0e558e5)


