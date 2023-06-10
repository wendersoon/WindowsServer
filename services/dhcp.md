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

5. A próxima janela defini-se as **exclusões de endereços** que não serão distribuídos. Por exemplo, se ali em cima eu tivesse adicionado a faixa de IP a partir de 192.168.0.1, certamente para não dá algum problema lá na frente, eu adicionaria o IP do servidor como uma exclusão. Mas como configurei no passo anterior de uma forma que deixe uma faixa de IPs livres para trabalharmos não faz-se necessário a exclusão, além do mais essa é uma prática recomendada.

6. Na janela seguinte, pede-se o tempo em que um IP ficará disponível para uma máquina. Esse tempo depende muito do ambiente na qual o servidor DHCP irá ser usado, por exempo, em uma praça de alimentação com fluxo enorme de pessoas não é nenhum pouco recomendável reservar um IP para um cliente por, digamos, 3 dias porque isso causaria problemas na conexão onde uma nova máquina não conseguiria obter um IP, por exemplo. Como estou em um ambiente de teste, irei deixar o padrão mesmo que é de 8 dias.

7. Nessa janela deixe esse opção marcada, porque iremos adicionar mais algumas configurações:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c11562f2-8d78-42a0-b178-02fc75644310)

8. Será pedido para adicionar o IP padrão do gateway, no meu caso é o `192.168.0.1`
9. Na próxima janela, é pedido para adicionar o IP do DNS. É recomendável adicionar como DNS primário o próprio IP do servidor, porque qualquer máquina na rede irá solicitar primeiro que resolva o nome no servidor local, e essa característica em conjunto com um firewall garante um segurança mais "fechada" a toda a infraestrutura. Veja como configurei o meu:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ffafb9ea-c270-4881-8d7b-3681e89e4c22)

10. Pule a janela `WINS Servers` que serve para configurações especifícas para computadores com Windows.
11. Na janela seguinte deixe marcado a opção `Yes, I want to activate this scope now`. E termine a configuração

Se o escopo não estiver ativado, basta clicar no ícone que aparece na imagem abaixo, ele deve está com a seta para baixo para está ativo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/f316ffb0-761f-4a35-87aa-4259af0052c2)




