# Servidor de Impressão

Neste artigo instalaremos e faremos a configuração de um servidor de impressão. De todos os serviços/funções que trabalhamos até o momento, este é o mais simples deles. Um servidor de impressão nada mais é que um intermediário entre os computadores dos usuários e as impressoras conectadas a rede. O servidor recebe as solicitações de impressão, verifica se as impressoras estão disponíveis e encaminha os trabalhos de impressão para impressora correta. 

Para exemplificar, imagine um escritório muito grande que tenha diversos funcionários, mais de 100, e cada um deles precisa utilizar a impressora para algum trabalho. O chefe sabendo que todos os computadores estão na mesma rede, decide colocar umas 5 impressoras para que todos pudessem usar. Ele espalha essas impressoras pela sala e apenas conecta-as a rede sem configurações a mais. Isso com certeza daria um problema, pois como um funcionário saberia em que impressora seu material seria impresso ou o computador pra que impressora mandar?

Para resolver problemas assim é que existe o servidor de impressão, pois ele gerencia todo o ecossistema que esteja atrelando as máquinas com as impressoras. Evitando, por exemplo, que você tenha de ir na máquina do usuário para cancelar alguma impressão errada etc.

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele(ou se quiser, apenas a parte da instalação), pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.***


# Instalação

Para instalar acesse seu Server Manager e vá na guia `Manage -> Add Rules and Features`, procure pela função `Print and Document Services`:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/726bb3b5-b560-4ec0-b1ef-d4183737c5f4)

Na janela semelhante a imagem abaixo, marcarei apenas a opção *Print Server*. As outras opções referem-se, respectivamente, a scanners, impressão via internet e suporte a sistemas operacionais baseados em Unix:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/348792b2-4cfa-451b-8ec7-8f430c540d03)

Não esqueça de salvar as configurações na sua pasta. Termine a instalação.

# Configuração


1. No Server Manage acesse a guia `Tools` e procure por `Print Management`:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/cc07ed39-9b92-4c5b-a8c4-c0972e758a84)

2. A tela inicial que teremos é a seguinte:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0d318ae1-0a38-4628-8f46-4ddc560ee947)

Aqui podemos adicionar os drives e as impressoras bem como as *GPO*s, isto é, as politicas de grupos etc. Temos também a opção de migrar servidores de impressão já existentes:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/8b9dac93-c3a9-44da-884a-9675580a0162)

3. Em `Print Servers` é onde fica reunido as máquinas que compõem o servidor de impressão. Veja na imagem abaixo que temos as seguintes opções: `Drivers` - drives para aquele servidor em específico, `Forms` - as formas de papel que podem ser impressas, `Ports` - as portas de cada impressora e `Prints` - são as impressoras.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2bb3f356-8019-44e7-ad4b-5c1c71c5dbcf)

4. Em `Prints` clique com o botão direito do mouse e vá em `Add Printer`:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/92791b9c-3048-4f46-949f-e3974412e3dd)


5. Nessa janela selecione a maneira pela qual deseja adicionar a impressora, pode ser via pesquisa na internet, via TCP/IP e também por porta:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/93f54852-c02f-4495-aee3-710e44a5ec4b)

6. Na janela seguinte adicione as seguintes configurações:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/bbdc4d3c-f057-4416-861d-a5dd3bcc8828)

Em `Type of Device` temos diversas maneiras de adicionar a impressora, fique a vontade para explorar. Note que estou usando apenas um IP aleatório para fins didáticos, pois não tenho impressora aqui para fazer um teste de fato.

7. Aguarde um pouco a aplicação detectar o dispositivo. Após isso pode aparecer a seguinte janela, apenas pule ela:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ef1d9d1a-2f8c-43d7-ab0f-4ec30447d153)

8. Na janela seguinte, se você não tiver o drive específico da impressora instalado no computador apenas deixe marcado a opção conforme a imagem:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/6f1b0d98-d58a-4563-99df-b80011ee05fd)

9. Aqui selecionamos o driver que vamos querer, em geral essa lista é bem completa mas se caso você não achar, pode adicionar em `Have Disk` o arquivo baixado do driver:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/84327685-d28c-436b-9005-dc5b6d53321b)

10. Na janela seguinte colocamos mais algumas informações como, por exemplo, o nome da impressora, o nome que vai ser compartilhado etc. Veja o exemplo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/578364d4-e887-45b3-84a2-3c5a57e38383)

Depois disso a impressora está instalada!
11. 


