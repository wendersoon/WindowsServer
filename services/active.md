# Controlador de Domínio

<div align="center">
  
<img src=https://github.com/wendersoon/WindowsServer/assets/104470835/9f3824b5-a399-4de1-a485-73e1dbc273fe  width="500" />

</div>

O Active Directory é um serviço de diretório desenvolvido pela Microsoft que funciona como um banco de dados centralizado para gerenciar e organizar recursos de rede, fornece uma estrutura hierárquica para armazenar informações sobre usuários, computadores, grupos e outros objetos. Ele implememta esse serviço no protocolo [LDAP](https://www.ibm.com/docs/pt-br/was-nd/8.5.5?topic=SSAW57_8.5.5/com.ibm.websphere.ihs.doc/ihs/cihs_ldap.htm). 

Iremos nesse artigo instalar e configurar o Active Directory(AD) e utilizar ele como controlador de domínio, e se você deseja saber mais sobre esse serviço acesse o site oficial pelo [link](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/get-started/virtual-dc/active-directory-domain-services-overview).

***OBS: Esse artigo faz parte de uma sequência, sendo que o primeiro serviço implementado foi o WEB. É importante que você já tenha lido ele, pois não irei repetir alguns passos de instalação ou configuração comuns a todos os serviços no Windows Server 2016.*** 

## Instalação

***OBS: Entenda que em cada passo de instalação é porque cliquei em `next`***

Como de praxe na instalação de funções no Windows Server 2016, para adicionar o **Active Directory** no servidor basta você acessar o `Manage -> Add Rules and Features` e localizar o serviço. Veja abaixo como ele aparece:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/6ef3982a-ecd1-47e8-8a06-efa8568c2f26)

Se você perceber, na tela de overview do serviço, ele fala que é possível integrar o AD com a Azure:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/65fe4e61-701b-4d16-abd1-8ae1ab54e9df)

Termine a instalação da função e não esqueça de exportar as configurações para um arquivo.

## Configuração

No painel principal do Server Manager, perceba que o ícone de notíficações deu um alerta, é aqui que fica o pós-instalação do AD:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/eacd0a1a-b7f3-4331-9eb2-9afc3916e741)

1. Clique em `Promote this server to a domain controler`, e selecionaremos a seguinte configuração:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0fc10af3-0cc1-46c8-b711-d721b8ef99de)

Observe que em `Select the deployment operation` existe três opções. A primeira refere-se quando queremos adicionar um controlador de domínio em um ambiente que já está todo configurado com seu próprio AD, ou seja, basicamento adicionaríamos um *domain controller secundário ou réplica*. A segunda opção se dá também no mesmo cenário da primeira, com a diferença que o nosso controlador de domínio seria implementado para ser um *sub-domínio*. E por último, a opção que marcamos, é quando queremos adicionar um controlador de domínio onde não existe um.

Veja também que em `Root domain name` coloquei `IFMA.WENDERSON`, você pode estar colocando qualquer outro padrão, por exemplo, `EMPRESA.SETOR`.

2. Na segunda etapa, ele vai pedir o nível funcional do domínio e o nível funcional de floresta. De maneira muito breve, o nível funcional de domínio leva em conta a existência de outros **controladores de domínios legados** na infraestrutura/rede, por exemplo, um controlador de domínio em Windows Server 2016 que está na mesma rede de um controlador de domínio com Windows Server 2003, o WS2016 terá o nível funcional do WS2003. 

Já o nível funcional de floresta são as features que teremos disponíveis para toda a infraestrutura do nosso domínio e sub-domínios (floresta). Geralmente, o nível funcional da floresta é definido pelo nível funcional do domínio mais baixo presente na floresta. Veja a imagem abaixo de como ficou a configuração nessa janela:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/d07e6841-1907-4aa5-a52e-e1ccbb181166)

Veja que desmarquei o servidor DNS porque não o temos instalado até o momento. Defina também a senha do serviço de restauração do Active Directory.

3. A próxima janela é onde definimos o nome do NetBIOS, se quiser você pode deixa a sugerida pelo serviço.

4. Na janela `Paths` é onde configuramos os locais que serão armazenados a base de dados, os arquivos de logs e as políticas. Eu deixei o padrão do sistema, mas você pode escolher outra se quiser.

5. Em `Review Options`, temos uma revisão das configurações que selecionamos durante o caminho.

6. Na próxima janela, o assitente vai verificar se precisar de algum pré-requisito para que nosso controlador funcione normalmente:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/515b14ec-79ef-4529-a6ca-9027c7cd4403)

7. Termine de instalar e após o processo o seu servidor irá reiniciar. Veja como a tela de login já mudou na reinicialização, o domínio que escolhemos aparecer anteposto o nome do perfil:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/f779cca1-a5c5-4498-ae35-cabe533f94b1)

8. Acesse o Server Manager e veja na guia `Tools` os atalhos disponíveis do Active Directory:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e78cfaa3-499e-431e-b976-0a17ebdd3937)

Veremos em outros artigos algumas dessas ferramentas.

---

Termino por aqui esse artigo. Obrigado pela leitura!





