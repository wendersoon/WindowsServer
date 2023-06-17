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

![244887456-2759b7d5-42f0-4f97-837e-3296a53c7655](https://github.com/wendersoon/WindowsServer/assets/104470835/8e9caf96-fb75-4d3b-8474-c63dc9289fba)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2759b7d5-42f0-4f97-837e-3296a53c7655)

Instale a função. Se você está em umáquina virtual, é recomendável configurar a rede da VM em modo NAT pra que não atrapalhe sua rede local real. E também não esqueça de exportar as features e rules selecionadas.

## Configuração

1. No Server Manager acesse a guia `Tools` e procure por DHCP:

![244889300-e1a63509-9624-41fa-a764-15f5fb5735da](https://github.com/wendersoon/WindowsServer/assets/104470835/91bbd055-e79e-4c21-8207-2b525023c491)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e1a63509-9624-41fa-a764-15f5fb5735da)

Observe no painel principal do DHCP Server(imagem abaixo) que do lado esquerdo estão as opções de configuração do IPv4 e IPv6 assim como configurações de policy e filters. Nesse artigo não trabalharemos com esses últimos, apenas com uma configuração básica para um rede minimamente funcional.

![244889422-a5e3253c-1b3b-4d89-bbf0-9a3d0c7ac1b8](https://github.com/wendersoon/WindowsServer/assets/104470835/3c844bd2-8362-4342-a4ab-8d192382d2bf)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/a5e3253c-1b3b-4d89-bbf0-9a3d0c7ac1b8)

2. A primeira coisa que devemos fazer é criar um escopo que nada mais é do que a faixa de endereços IPs que quero distribuir. Clicando com o botão direito do mouse em IPv4, selecione `New Scope`

![244889968-98502e5a-61b4-4280-8c36-ced5917d3eae](https://github.com/wendersoon/WindowsServer/assets/104470835/ccdf938d-d006-4f49-9423-6ebd6f20527b)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/98502e5a-61b4-4280-8c36-ced5917d3eae)

3. A primeira janela que aparece pede apenas um nome e uma descrição para o novo escopo que estamos criando, então fique livre pra adicionar o nome que quiser. Em um ambiente de produção é recomendável formatar esses nomes seguindo um padrão, por exemplo, *WIFI-FINANCEIRO* etc.

4. Na próxima janela adicionamos o range de endereços que o servidor DHCP irá entregar, veja como configurei o meu:

![244890171-0163d6ad-ee0b-47ac-8756-227819de43d9](https://github.com/wendersoon/WindowsServer/assets/104470835/9fd79996-5050-4c54-b440-0ac7854b279b)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0163d6ad-ee0b-47ac-8756-227819de43d9)

5. A próxima janela defini-se as **exclusões de endereços** que não serão distribuídos. Por exemplo, se ali em cima eu tivesse adicionado a faixa de IP a partir de 192.168.0.1, certamente para não dá algum problema lá na frente, eu adicionaria o IP do servidor como uma exclusão. Mas como configurei no passo anterior de uma forma que deixe uma faixa de IPs livres para trabalharmos não faz-se necessário a exclusão, além do mais essa é uma prática recomendada.

6. Na janela seguinte, pede-se o tempo em que um IP ficará disponível para uma máquina. Esse tempo depende muito do ambiente na qual o servidor DHCP irá ser usado, por exempo, em uma praça de alimentação com fluxo enorme de pessoas não é nenhum pouco recomendável reservar um IP para um cliente por, digamos, 3 dias porque isso causaria problemas na conexão onde uma nova máquina não conseguiria obter um IP, por exemplo. Como estou em um ambiente de teste, irei deixar o padrão mesmo que é de 8 dias.

7. Nessa janela deixe esse opção marcada, porque iremos adicionar mais algumas configurações:

![244894724-c11562f2-8d78-42a0-b178-02fc75644310](https://github.com/wendersoon/WindowsServer/assets/104470835/0cfdd54c-a0c0-4293-9c31-855314436ea9)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c11562f2-8d78-42a0-b178-02fc75644310)

8. Será pedido para adicionar o IP padrão do gateway, no meu caso é o `192.168.0.1`
9. Na próxima janela, é pedido para adicionar o IP do DNS. É recomendável adicionar como DNS primário o próprio IP do servidor, porque qualquer máquina na rede irá solicitar primeiro que resolva o nome no servidor local, e essa característica em conjunto com um firewall garante um segurança mais "fechada" a toda a infraestrutura. Veja como configurei o meu:

![244894920-ffafb9ea-c270-4881-8d7b-3681e89e4c22](https://github.com/wendersoon/WindowsServer/assets/104470835/eeeee1c1-385b-4415-8b75-607194504276)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ffafb9ea-c270-4881-8d7b-3681e89e4c22)

10. Pule a janela `WINS Servers` que serve para configurações especifícas para computadores com Windows.
11. Na janela seguinte deixe marcado a opção `Yes, I want to activate this scope now`. E termine a configuração

12. Se o escopo não estiver ativado, basta clicar no ícone que aparece na imagem abaixo, ele deve está com a seta para baixo para está ativo:

![244895306-f316ffb0-761f-4a35-87aa-4259af0052c2](https://github.com/wendersoon/WindowsServer/assets/104470835/94942613-fcee-4e9e-9fda-aea7d61c92d4)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/f316ffb0-761f-4a35-87aa-4259af0052c2)

13. Agora precisamos autorizar o servidor DHCP no nosso controlador de domínio que configuramos no artigo anterior do Active Directory. Precisamos fazer isso porque configuramos um ambiente de domínio, e agora tudo que fizermos precisa de autorização de um usuário administrador do domínio. Isso é bom, pois garante maior controle da infraestrutura e, claro, evita de intrusos quererem bagunçar o servidor.

Voltando no painel principal do Server Manager, temos o ícone de notificação com alerta. Abra e clique em `Complete DHCP configuration`:

![244897670-cd62896e-0927-451e-a67f-86a7fdd5ba69](https://github.com/wendersoon/WindowsServer/assets/104470835/a426d9b0-d07b-44a1-8757-e57dea145768)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/cd62896e-0927-451e-a67f-86a7fdd5ba69)

Na janela que vai abrir clique em `next` e na outra clique em `commit`. E temos no servidor DHCP autorizado no domínio:

![244897781-566c935c-5d2d-4b7a-99f3-0c55ea3dfb20](https://github.com/wendersoon/WindowsServer/assets/104470835/5099ab14-6076-4ed0-8735-1def63ac257c)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/566c935c-5d2d-4b7a-99f3-0c55ea3dfb20)


## Teste do Servidor


Para vermos as estatísticas do servidor, basta clicar com o botão direito do mouse sobre o escopo e clicar em `Display Statistics`. Veja abaixo o resultado do meu:

![244898047-b532b140-33cb-4a61-ae2d-dc087a188882](https://github.com/wendersoon/WindowsServer/assets/104470835/162ea6ff-0e88-42b8-9437-94a23360afe3)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/b532b140-33cb-4a61-ae2d-dc087a188882)

Dos 181 IP's disponíveis, o servidor está entregando endereços para 3 máquinas. Isso significa que está funcionando corretamente.

---

Terminamos por aqui esse artigo. Agradeço pela leitura!


