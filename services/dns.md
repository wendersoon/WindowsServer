# Servidor DNS

<div align="center">

![244940300-1a913f46-9113-4502-9a42-734f9ec36bf1](https://github.com/wendersoon/WindowsServer/assets/104470835/5bb1e6ad-fa0c-41c6-898d-af9672b89854)

<img src = https://github.com/wendersoon/WindowsServer/assets/104470835/1a913f46-9113-4502-9a42-734f9ec36bf1 width="500" />

</div>

  
Para começarmos precisamos enteder o **DNS** (Domain Name System) que é um sistema de nomenclatura de domínios que atribui nomes **amigáveis e fáceis** de lembrar a endereços IP numéricos, que são usados para identificar servidores e dispositivos na internet. Em vez de digitar uma sequência de números para acessar um site ou serviço, o DNS permite que os usuários simplesmente digitem um nome de domínio, como "google.com", e o sistema se encarrega de traduzir esse nome em um endereço IP correspondente. Imagina se toda que você precisasse acessar um site tivesse de lembrar o IP dele, atualmente isso é impossível e ainda bem que há o serviço DNS. Para saber mais veja esse [artigo](https://www.cloudflare.com/pt-br/learning/dns/what-is-dns/) da Cloudflare que oferece um dos maiores serviços de DNS do mundo.<br>

Neste artigo instalaremos e faremos a configuração do nosso servidor DNS.

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele(ou se quiser, apenas a parte da instalação), pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.***

## Instalação

Para instalar acesse seu Server Manager e vá na guia `Manage -> Add Rules and Features`, procure pelo serviço *DNS Server* como no print abaixo:

![244940782-ba33f57a-1ce8-4422-8e70-619ac6f5dc1a](https://github.com/wendersoon/WindowsServer/assets/104470835/9d2f9ac1-a6a7-47e3-92d7-6bb4f4e4e23f)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ba33f57a-1ce8-4422-8e70-619ac6f5dc1a)

Não esqueça de salvar as configurações na sua pasta. Termine a instalação.

## Configuração

1. Nas configurações de rede do servidor faça a seguinte configuração(lembre-se que configuramos inicialmente no segundo artigo dessa sequência):

![244942429-65b89385-9199-4ac3-8729-07a901f47878](https://github.com/wendersoon/WindowsServer/assets/104470835/bc86d74e-8ad3-497c-9f8f-a92e5260f6ea)

![Screencast from 11-06-2023 11_00_45](https://github.com/wendersoon/WindowsServer/assets/104470835/65b89385-9199-4ac3-8729-07a901f47878)

É interessante adicionar o sufixo do DNS com o mesmo nome que você colocou como domínio no Active Directory. 

2. No Server Manager acesse a guia `Tools` e procure por DNS:

![244941191-2cea6881-c115-45d3-88e6-5867c0e558e5](https://github.com/wendersoon/WindowsServer/assets/104470835/a4b4692d-083a-4016-ba8c-6e5472a3be96)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2cea6881-c115-45d3-88e6-5867c0e558e5)

3. Ao acessar o DNS, o primeiro painel apresentado é como o do print abaixo:

![244942988-0eb986d0-3200-4b04-82a2-2c994d8aa673](https://github.com/wendersoon/WindowsServer/assets/104470835/21578003-6d3e-4ca7-ae82-f662769fe047)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0eb986d0-3200-4b04-82a2-2c994d8aa673)

* `Forward Lookup Zone`: é onde configuramos uma área de pesquisa direta no DNS. Ele mapeia nomes de domínio para endereços IP;
* `Reverse Lookup Zones`: configuramos uma área de pesquisa reversa no DNS. Ao contrário de uma zona de pesquisa direta, onde você procura um endereço IP para obter o nome de domínio correspondente, uma zona de pesquisa reversa permite pesquisar o nome de domínio correspondente a um endereço IP;
* `Trust Points`: os "pontos de confiança" são usados no DNS para estabelecer confiança entre diferentes domínios Por meio de trust points, um domínio pode delegar a autoridade para a resolução de nomes a outro domínio confiável;
* `Conditional Forwarders`: são as configurações que permitem que um servidor DNS encaminhe solicitações para um servidor DNS específico com base em condições definidas; 
* `Root Hints`: são informações de configuração do servidor DNS que ajudam a resolver nomes de domínio quando o servidor não tem as informações em cache;
* `Forwarders`: são servidores DNS para os quais o servidor DNS local encaminha todas as consultas não resolvidas internamente. 

4. Clique em `Forward Lookup Zone`. Se você configurou o Active Directory anteriormente, irá aparecer as zonas de DNS já configuradas e sincronizadas aqui, veja a imagem abaixo. Mas para efeito didático, iremos adicionar uma nova zona no nosso servidor então clique com o botão direito do mouse em  `Forward Lookup Zone` e selecione `New Zone`.

![244944194-913ecb9e-f317-404e-aefb-a82aa08e3c25](https://github.com/wendersoon/WindowsServer/assets/104470835/b97bd8df-65af-4835-9a59-03297c2041a1)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/913ecb9e-f317-404e-aefb-a82aa08e3c25)

5. Na primeira janela que aparece clique em `next`. Na janela seguinte deixe as configurações da forma padrão como o print abaixo: 

![244944572-086e78af-a581-4133-9533-7f64feaebbf5](https://github.com/wendersoon/WindowsServer/assets/104470835/47f0010a-626e-4bdc-b584-36d0f9475ea4)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/086e78af-a581-4133-9533-7f64feaebbf5)

Se você não configurou o Active Directory, a última caixa de seleção não estará disponível. Essa configuração é apenas para integrar a zona no AD.

6. Na janela seguinte deixe a configuração padrão marcada:

![244944745-759058ee-9ee7-4df0-ab79-4afa4c7ac24c](https://github.com/wendersoon/WindowsServer/assets/104470835/29969289-a0ce-409d-ad03-fb65f229e334)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/759058ee-9ee7-4df0-ab79-4afa4c7ac24c)

7. Será pedido um nome para a nova zona que está sendo configurada, para diferenciar eu irei colocar o nome *IFMA.WENDERSON.LOCAL*. Você deve também configurar um nome diferente do domínio criado no Active Directory.

8. Na próxima janela selecione o tipo de atualização do DNS. Deixe marcado essa opção para ter atualização dos registros tanto de máquinas microsoft quanto de máquinas não-microsoft.

![244944892-25481fa6-0c39-48af-a045-361705034052](https://github.com/wendersoon/WindowsServer/assets/104470835/417272c7-484f-47d6-bc44-e045325aa5dc)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/25481fa6-0c39-48af-a045-361705034052)

Para a criação de zonas reversas segue-se o mesmo padrão com a diferença que teremos de adicionar o IP em determinada janela.


## Teste do Servidor

***OBS: Se você fizer o teste na sua máquina real, lembre-se de configurar sua rede para que responda ao DNS do seu servidor!***

Irei utilizar a zona configurada automaticamente quando trabalhamos com o Active Directory. O nome para meu ip pode ser achado da seginte forma:

![244947037-dd9fd69f-0c7d-478c-ac9b-c41aea72cd9f](https://github.com/wendersoon/WindowsServer/assets/104470835/eb66c79e-f6b3-4bbf-9166-89634eac1dd7)

![Screencast from 11-06-2023 12_09_43](https://github.com/wendersoon/WindowsServer/assets/104470835/dd9fd69f-0c7d-478c-ac9b-c41aea72cd9f)

Utilizando esse nome, o primeiro teste que farei é com o `nslookup` no terminal do meu ubuntu, veja o resultado:

![244946734-869d4ce8-49ff-4e99-a936-5c46a3af2b57](https://github.com/wendersoon/WindowsServer/assets/104470835/d1743aa1-26cd-45e4-8b90-8cf1d417ca25)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/869d4ce8-49ff-4e99-a936-5c46a3af2b57)

Isso mostra que está resolvendo o nome para o IP da minha máquina.

Agora vamos acessar o site que configuramos no artigo do servidor web. Colocaremos o mesmo nome para ser resolvido, acrescetando apenas a porta 8080 que configuramos lá. 

![244946571-76066678-9135-4bfc-a39f-e7fc6de39e72](https://github.com/wendersoon/WindowsServer/assets/104470835/017000be-2657-46b6-8cb5-7917b4fe9580)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/76066678-9135-4bfc-a39f-e7fc6de39e72)

E funcionou corretamente! :)

---

Terminamos por aqui esse artigo. Obrigado pela leitura!




