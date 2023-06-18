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

