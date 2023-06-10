# Servidor DHCP

<div align="center">

![istockphoto-1287005334-170667a-removebg-preview](https://user-images.githubusercontent.com/104470835/232313043-ad7be7d3-28e5-43da-8403-ac9f8d311ac1.png)

</div>

O DHCP (**Dynamic Host Configuration Protocol**) é um protocolo de rede que permite que um servidor atribua automaticamente endereços IP e outras configurações de rede para dispositivos em uma rede. Em vez de ter que configurar manualmente cada dispositivo com um endereço IP, gateway padrão, servidor DNS, entre outras configurações, o DHCP simplifica esse processo, tornando-o mais automatizado e eficiente.

Quando um dispositivo é conectado a uma rede que usa o DHCP, ele solicita uma configuração de rede ao servidor DHCP. O servidor DHCP responde com um endereço IP disponível, que é então atribuído ao dispositivo que solicitou. Além do endereço IP, o servidor DHCP também pode fornecer outras configurações de rede, como o gateway padrão, a máscara de sub-rede, os servidores DNS, entre outros.

Imagina se não houvesse o DHCP, essas configurações seriam todas manuais. Em um único computador éfácil configurar, mas em redes que existem muitos dispositivos torna-se um trabalho cansativo e demorado. 

Neste artigo iremos instalar e configurar nosso próprio DHCP, se caso você quiser saber mais sobre esse assunto veja esse [artigo](https://learn.microsoft.com/pt-br/windows-server/networking/technologies/dhcp/dhcp-top).

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele(ou se quiser, apenas a parte da instalação), pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.***

## Instalação

Para instalar acesse seu Server Manager e vá na guia `Manage -> Add Rules and Features`, procure pelo serviço *DHCP Server* como no print abaixo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2759b7d5-42f0-4f97-837e-3296a53c7655)

Instale a função. Se você está em umáquina virtual, é recomendável configurar a rede da VM em modo NAT pra que não atrapalhe sua rede local real. E também não esqueça de exportar as features e rules selecionadas.

## Configuração

1. No Server Manager acesse a guia `Tools` e procure por DHCP:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e1a63509-9624-41fa-a764-15f5fb5735da)

Observe no painel principal do DHCP Server(imagem abaixo) que do lado esquerdo estão as opções de configuração do IPv4 e IPv6 assim como configurações de policy e filters. Nesse artigo não trabalharemos com esses últimos, apenas com uma configuração básica para um rede minimamente funcional.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/a5e3253c-1b3b-4d89-bbf0-9a3d0c7ac1b8)

2. A primeira coisa que devemos fazer é criar um escopo que nada mais é do que a faixa de endereços IPs que quero distribuir. Clicando com o botão direito do mouse em IPv4, selecione `New Scope`

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/98502e5a-61b4-4280-8c36-ced5917d3eae)

3. A primeira janela que aparece pede apenas um nome e uma descrição para o novo escopo que estamos criando, então fique livre pra adicionar o nome que quiser. Em um ambiente de produção é recomendável formatar esses nomes seguindo um padrão, por exemplo, *WIFI-FINANCEIRO* etc.

4. Na próxima janela adicionamos o range de endereços que o servidor DHCP irá entregar, veja como configurei o meu:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0163d6ad-ee0b-47ac-8756-227819de43d9)

5. A próxima janela defini-se as exclusões de endereços que não serão distribuídos. Por exemplo, se ali em cima eu tivesse adicionado a faixa de IP a partir de 192.168.0.1, certamente para não dá algum problema lá na frente, eu adicionaria o IP do servidor como uma exclusão. Mas configurei no passo anterior de uma forma que deixe uma faixa de IPs livres para trabalharmos, essa é uma prática recomendada.




