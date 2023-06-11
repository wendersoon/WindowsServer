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

2. No Server Manager acesse a guia `Tools` e procure por DNS:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2cea6881-c115-45d3-88e6-5867c0e558e5)

3. Ao acessar o DNS, o primeiro painel apresentado é como o do print abaixo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0eb986d0-3200-4b04-82a2-2c994d8aa673)

* `Forward Lookup Zone`: é onde configuramos uma área de pesquisa direta no DNS. Ele mapeia nomes de domínio para endereços IP;
* `Reverse Lookup Zones`: configuramos uma área de pesquisa reversa no DNS. Ao contrário de uma zona de pesquisa direta, onde você procura um endereço IP para obter o nome de domínio correspondente, uma zona de pesquisa reversa permite pesquisar o nome de domínio correspondente a um endereço IP;
* `Trust Points`: os "pontos de confiança" são usados no DNS para estabelecer confiança entre diferentes domínios Por meio de trust points, um domínio pode delegar a autoridade para a resolução de nomes a outro domínio confiável;
* `Conditional Forwarders`: são as configurações que permitem que um servidor DNS encaminhe solicitações para um servidor DNS específico com base em condições definidas; 
* `Root Hints`: são informações de configuração do servidor DNS que ajudam a resolver nomes de domínio quando o servidor não tem as informações em cache;
* `Forwarders`: são servidores DNS para os quais o servidor DNS local encaminha todas as consultas não resolvidas internamente. 

4. Clique em `Forward Lookup Zone`. Se você configurou o Active Directory anteriormente, irá aparecer as zonas de DNS já configuradas e sincronizadas aqui, veja a imagem abaixo. Mas para efeito didático, iremos adicionar uma nova zona no nosso servidor então clique com o botão direito do mouse em  `Forward Lookup Zone` e selecione `New Zone`.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/913ecb9e-f317-404e-aefb-a82aa08e3c25)

5. Na primeira janela que aparece clique em `next`. Na janela seguinte deixe as configurações da forma padrão como o print abaixo: 

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/086e78af-a581-4133-9533-7f64feaebbf5)

Se você não configurou o Active Directory, a última caixa de seleção não estará disponível. Essa configuração é apenas para integrar a zona no AD.

6. Na janela seguinte deixe a configuração padrão marcada:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/759058ee-9ee7-4df0-ab79-4afa4c7ac24c)

7. Será pedido um nome para a nova zona que está sendo configurada, para diferenciar eu irei colocar o nome *IFMA.WENDERSON.LOCAL*. Você deve também configurar um nome diferente do domínio criado no Active Directory.

8. Na próxima janela selecione o tipo de atualização do DNS. Deixe marcado essa opção para ter atualização dos registros tanto de máquinas microsoft quanto de máquinas não-microsoft.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/25481fa6-0c39-48af-a045-361705034052)

Para a criação de zonas reversas segue-se o mesmo padrão com a diferença que teremos de adicionar o IP em determinada janela.




