# Sobre o Server Manager

Antes de iniciarmos as instalações e configurações dos serviços do nosso servidor é interessante, ou melhor dizendo, é necessário sabermos o que é o **Server Manager** porque o usaremos durante todo o nosso projeto e também para não ficar repetitivo algumas funções encontradas nele.

O **Server Manager**(gerenciador de servidor) segundo a própria definição encontrada no [site oficial](https://learn.microsoft.com/pt-br/windows-server/administration/server-manager/server-manager) é *"é um console de gerenciamento do Windows Server que ajuda a provisão de profissionais de TI e o gerenciamento local e remoto de servidores baseados em Windows de seus desktops"*. Em resumo é uma ferramenta implementada pela Microsoft para facilitar a administração de servidores locais e remotos. Também segundo o próprio site acima, essa ferramenta pode ser usada para gerenciar até **100 SERVIDORES** dependendo da carga de trabalho que estão sendo usados. 

Vejamos as funcionalidades nos tópicos abaixo.

## Interface Gráfica do Usuário (GUI)

Encontramos o **Server Manager** no menu iniciar, como vimos no *artigo anterior*. A primeira janela que vemos ao abrir a ferramenta é a seguinte:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/772c8260-c19a-4f1d-8fad-299f17dab341)

Agora veremos cada uma das guias que podemos observar nessa janela principal. Começaremos pelas guias do lado esquerdo:

* `Dashboard`: essa guia exibe uma visão geral do servidor selecionado. Ela fornece informações resumidas sobre o status do servidor, alertas, notificações e tarefas comuns de gerenciamento. É um ponto central para obter uma **visão geral rápida** do estado geral do servidor;

* `Local Server`: essa guia contém informações e configurações específicas do **servidor local**. Aqui podemos visualizar e modificar as configurações do servidor (*fizemos isso no artigo anterior*), como o nome do computador, o grupo de trabalho ou domínio ao qual o servidor pertence, o estado do Firewall do Windows, a ativação do Windows, configurações de atualização automática, configurações de acesso remoto etc.

* `All Servers`: permite gerenciar vários servidores a partir de um único console. Ela exibe uma lista de todos os servidores que estamos gerenciando e fornece uma visão geral do status de cada servidor. A partir desta guia, pode se executar ações em servidores individuais ou em grupos de servidores, como adicionar e remover funções, reiniciar servidores, verificar o status de atualizações etc.

* `File and Storage Services`: essa guia é usada para gerenciar funções e recursos relacionados a arquivos e armazenamento. Ela permite configurar e gerenciar compartilhamentos de arquivos, serviços de replicação de arquivos, serviços de acesso a arquivos, serviços de armazenamento em nuvem entre outros.

Agora veremos as seguintes guias:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c504bbf5-2a8d-4e12-813d-3242e7ad9b7e)

* `Manage`: essa guia fornece acesso a configurações importantes em um gerenciamento de servidor tais como: adicionar/remover funções e recursos, adicionar servidores, criar grupos de servidores e acessar as propriedades do gerenciador do servidor. Veja a guia aberta abaixo.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/f338f6d6-f318-4760-89e0-3d8b54124759)

* `Tools`: nessa guia temos acesso as nossas ferramentas
