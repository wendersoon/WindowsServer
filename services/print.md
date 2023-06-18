# Servidor de Impressão

Neste artigo instalaremos e faremos a configuração de um servidor de impressão. De todos os serviços/funções que trabalhamos até o momento, este é o mais simples deles. Um servidor de impressão nada mais é que um intermediário entre os computadores dos usuários e as impressoras conectadas a rede. O servidor recebe as solicitações de impressão, verifica se as impressoras estão disponíveis e encaminha os trabalhos de impressão para impressora correta. 

Para exemplificar, imagine um escritório muito grande que tenha diversos funcionários, mais de 100, e cada um deles precisa utilizar a impressora para algum trabalho. O chefe sabendo que todos os computadores estão na mesma rede, decide colocar umas 5 impressoras para que todos pudessem usar. Ele espalha essas impressoras pela sala e apenas conecta-as a rede sem configuração a mais. Isso com certeza daria um problema, pois como um funcionário saberia em que impressora seu material seria impresso?

Para resolver problemas assim é que existe o servidor de impressão

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele(ou se quiser, apenas a parte da instalação), pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.***

