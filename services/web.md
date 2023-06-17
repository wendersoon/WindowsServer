# Servidor WEB

<div align = "center">
 
![243180626-30ac9ec0-faca-4980-8ae4-60f8d5d78392](https://github.com/wendersoon/WindowsServer/assets/104470835/b6e36001-7f8b-43ae-8781-a1007317fabf)


![iis-logo-blue](https://github.com/wendersoon/WindowsServer/assets/104470835/30ac9ec0-faca-4980-8ae4-60f8d5d78392)

 </div>


Nesse artigo instalaremos o utilitário que permite termos um servidor web ativo. Esse utilitário é chamado no windows de **IIS (Internet Information Services)** que é um conjunto de serviços de servidor web fornecido pela Microsoft, ele também permite hospedar sites e aplicativos na web, oferecendo recursos avançados de segurança, gerenciamento e desempenho, além de, oferecer suporte a vários protocolos e serviços da web, como HTTP, HTTPS, FTP, FTPS, SMTP e NNTP. Ele é uma escolha popular entre os desenvolvedores que trabalham com a plataforma do Windows. Se você quiser saber mais sobre essa ferramenta, acesse o site oficial nesse [link](https://www.iis.net/). 

## Instalação

Para instalar o ISS ou qualquer outro serviço deve-se seguir os seguintes passos:

1. Ir em `Manage -> Add Rules and Features`. Se é a primeira vez que você abre essa janela irá aparecer uma janela chamada de "Before you begin" que é apenas uma janela informativa, você pode marcar a caixa de skip logo abaixo para pular sempre que abrir novamente esse menu e é isso que faremos. 

*OBS: Para não tornar-se repetitivo, toda vez que concluirmos uma configuração numa janela estará subentendido que clicamos em `next`, a não ser que eu cite outro botão.*

2. Na janela seguinte ("Instalation Type") é pedido basicamente duas coisas, se você que fazer a instalação em um servidor remoto ou local. No nosso caso é no servidor local então deixamos marcado a seguinte opção:

![243183220-81b5dbf2-e801-4ae9-bf3c-53dbbb12b8df](https://github.com/wendersoon/WindowsServer/assets/104470835/4ab2b53f-1d0c-49f9-940b-ae39568ce94f)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/81b5dbf2-e801-4ae9-bf3c-53dbbb12b8df)

3. Na próxima janela ("Server Selection") é onde selecionamos nosso servidor (sim, isso mesmo kkkk), como tenho apenas um servidor ativo é só ele que irá aparecer.
4. A janela seguinte do assistente é onde de fato adicionamos o serviço/função que desejo instalar. Nela estão listadas muitos serviços, procuraremos por `Web Server (ISS)` como na imagem abaixo:

![243183898-eb4bf52b-639b-4d19-bb44-76c9ab11cdc8](https://github.com/wendersoon/WindowsServer/assets/104470835/b590d6ea-b1c9-464c-9a5b-43fd5ed1906d)


![image](https://github.com/wendersoon/WindowsServer/assets/104470835/eb4bf52b-639b-4d19-bb44-76c9ab11cdc8)

Se você observar, no lado direito irá sempre aparecer uma breve descrição daquilo que selecionamos. Ao marcar a caixa de diálogo do lado do serviço irá aparecer uma pequena janela pedindo para adicionar requisitos obrigatórios para que o serviço funcione corretamente e é isso que queremos, então bastar clicar em `Add Features`.

5. Na janela "Features" é onde podemos selecionar alguns recursos a mais para adicionar ao servidor, como por exemplo, recursos para NFS, SMPT etc.. E também, se você já observou, já existem algumas que veêm por padrão no Windows. Nessa janela não selecionaremos nenhuma feature por enquanto.
6. A próxima janela é apresentado um pequeno resumo da função que iremos instalar, além de colocar no rodapé um link para que saibamos mais sobre aquele serviço.
7. A janela "Role Services" é onde adicionaremos serviços da nossa função, no caso, serviços que comporão o *Web Server(ISS)*, veja na imagem abaixo os que instalaremos:

![243185936-54b348de-6cc8-4079-a8d6-379c362503be](https://github.com/wendersoon/WindowsServer/assets/104470835/385717d7-da32-44c3-acc0-d4a76a0f3e7a)

![Sem título (1)](https://github.com/wendersoon/WindowsServer/assets/104470835/54b348de-6cc8-4079-a8d6-379c362503be)

Para efeito didático, não abordarei cada uma delas aqui pois isso alongaria demais o artigo. Mas se você quiser entender cada um, poderar está lendo as descrições que aparecem na lateral e fazendo suas pesquisas.
8. Na janela "Confirmation" abaixo é apresentado um resumo de tudo que iremos instalar, também é interessante salvarmos essas configurações se caso precisarmos fazer alguma auditoria futura, então para isso clicamos em `Export configuration settings`. Irei criar uma pasta específica para salvar esses documentos, você aí pode está fazendo como quiser. 

![243186680-e8823e9f-a68b-4dc4-bbda-d2210c2b3efc](https://github.com/wendersoon/WindowsServer/assets/104470835/306174c0-0c6c-41f2-b14a-29843ba2ffff)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e8823e9f-a68b-4dc4-bbda-d2210c2b3efc)

Após salvar o documento, clique em `Install` e aguarde o processo de instalação ser concluído, após isso feche a janela.

Na guia `Tools`, toda vez que instalarmos alguma função nova ela será listada ali, veja como o **Web Server ISS** aparece:

![243187725-d9c0483c-b43b-4812-8572-a8d24541b263](https://github.com/wendersoon/WindowsServer/assets/104470835/f0ad5d93-b571-4bdf-adad-bf383d0402aa)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/d9c0483c-b43b-4812-8572-a8d24541b263)

## Teste do Servidor

O primeiro teste que devemos fazer é acessar o IP pela porta 80 em navegador, se espera que veja a página padrão do IIS. Veja abaixo o resultado:

![244503982-a7d27a4c-507f-48ca-9c3f-379f0d4f981d](https://github.com/wendersoon/WindowsServer/assets/104470835/22f96211-3c6a-4a35-a001-1a721e825454)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/a7d27a4c-507f-48ca-9c3f-379f0d4f981d)

Agora vejamos a interface e as configurações disponíveis no ISS e os serviços adicionais que instalamos (lembrando que para você acessar o IIS, basta ir em `Tools` e acessar a função). 

Quando clicarmos, nos depararemos com uma janela apresentando diversas informações sobre a aplicação, essa primeira parte é chamada de `Start Page`. Nós queremos as configurações relacionas ao **nosso servidor**, por isso vamos clicar no nome dele na parte esquerda da janela como na imagem abaixo:

![244508381-c75119cd-4459-40f3-bc3e-b3c7f79bcd48](https://github.com/wendersoon/WindowsServer/assets/104470835/6a0fedc2-2313-4f49-a558-ad7dabfc3e38)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c75119cd-4459-40f3-bc3e-b3c7f79bcd48)

Depois disso temos o seguinte painel:

![244512373-fe258698-5d5b-4d1f-a84b-d83d20a6e90f](https://github.com/wendersoon/WindowsServer/assets/104470835/eaba2406-6325-4d8e-9293-a357ad8a9216)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/fe258698-5d5b-4d1f-a84b-d83d20a6e90f)

São muitos os serviços apresentados nessa instalação básica, muitos deles são intuitivos outros exigem mais conhecimento técnico. Porém, neste artigo, não veremos todos eles porque o meu objetivo aqui é apresentar a ferramenta e um tutorial básico de seu uso. Você pode está aprofudando os seus conhecimentos atráves do site oficial que contém mais detalhes de cada "canto" dessa função. Novamento deixo aqui o link do [site oficial](https://www.iis.net/).

Se você abrir a seta ao lado do nome do servidor verá algumas aplicações associadas como, por exemplo, a da impressora e também uma pasta que irá conter os sites. E se você tiver curiosidade, ao clicar na página padrão, verá que o painel que aparece é bem semelhante ao painel anterior quando clicamos no nome do servidor. Evidemente, o painel anterior refere-se as configurações gerais do servidor enquanto o painel do site refere-se as configuraçãos do próprio site. Veja abaixo um print do painel do site:

![244515704-62a26d13-1399-4b27-8b39-1084385c78f7](https://github.com/wendersoon/WindowsServer/assets/104470835/b888ee45-156b-4405-aae4-7fdf93a920a5)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/62a26d13-1399-4b27-8b39-1084385c78f7)

### Criando Novo Site

Agora vamos adicionar um novo site, para isso iremos clicar com o botão direito do mouse em cima do servidor e em seguida clicar em `Add Website...`. Após isso irá aparecer uma janela como a do print abaixo, adicione as informações que são pedidas(pode ser igual da imagem). 

*Atenção em dois detalhes: O primeiro é de escolher uma porta que nenhum serviço esteja utilizando no momento. E o segundo é que o caminho que escolhi (`C:\inetpub\wwwroot\`) é o padrão do IIS e se você explorar encontrará os arquivos do site que vimos anteriormente no primeiro teste. O que fiz na imagem abaixo foi apenas criar uma pasta especifíca ali dentro para o meu novo site*

![244520080-301c5159-f591-4d60-845b-c8dbef544985](https://github.com/wendersoon/WindowsServer/assets/104470835/dee200e7-8b50-44f2-8331-3e23462c839e)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/301c5159-f591-4d60-845b-c8dbef544985)

Agora vamos acessar a pasta e lá dentro criar um arquivo html para nosso site. Para facilitar você pode copiar o arquivo do site padrão para a pasta e depois editar com o código que você quiser. Abaixo o html que usei:

```
<!DOCTYPE html>
<html>
<head>
  <title>Novo Site</title>
  <style>
    .center {
      text-align: center;
      margin-top: 50vh;
      transform: translateY(-50%);
    }
  </style>
</head>
<body>
  <div class="center">
    <h1>Novo Site</h1>
  </div>
</body>
</html>
```
O próximo passo é permitir no firewall o acesso externo na porta que configuramos, no caso a porta 8080. Primeiro pesquise no menu iniciar por "firewall" e clique no ícone como da imagem abaixo:

![244526646-59c052ae-ec36-4179-9077-138d835b1f7f](https://github.com/wendersoon/WindowsServer/assets/104470835/2ace096d-a381-4ca0-a566-d9b8031ca66f)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/59c052ae-ec36-4179-9077-138d835b1f7f)

Em seguida vá em `Inbound Rules` -> `New Rule...`:

![244527695-9b1dc000-106e-449e-881a-baca1a6577a9](https://github.com/wendersoon/WindowsServer/assets/104470835/3a1532a4-cf89-4b39-bf33-d7880cb14785)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/9b1dc000-106e-449e-881a-baca1a6577a9)

Escolha em `Rule Type` o tipo para porta, em `Protocol and Ports` adicione a porta 8080:

![244528076-cc77f9b8-7e78-419a-972a-ad7d613cc85b](https://github.com/wendersoon/WindowsServer/assets/104470835/eb23452c-01e9-4698-a3bc-b29d866595ff)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/cc77f9b8-7e78-419a-972a-ad7d613cc85b)

Clique em `next` até o último painel. Dê um nome a essa nova configuração e salve.

Se tudo deu certo podemos acessar agora pelo navegador com a respectiva porta. Vejamos o resultado abaixo:

![244528418-6aaa89d6-d2b8-4696-8be7-ab720e5b9c15](https://github.com/wendersoon/WindowsServer/assets/104470835/1321b74e-e382-4904-8837-69d48564ddc3)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/6aaa89d6-d2b8-4696-8be7-ab720e5b9c15)

### Certificado SSL Autoassinado

A segurança na rede é algo essencial e as certificações são necessárias para se ter o mínimo de um tráfego seguro. Vamos implemetar um certificado SSL autoassinado para nosso site. Se você não sabe o que é uma certificação SSL, acesse esse [artigo](https://www.hostinger.com.br/tutoriais/o-que-e-ssl-tls-https) que explica detalhadamente esse assunto.

Acesse as configurações do servidor e clique em `Server Certificates`:

![244529855-57513ab5-2add-421b-883c-da3e7af59989](https://github.com/wendersoon/WindowsServer/assets/104470835/f83cd995-3a1f-4ff1-9bde-9547f8dcbaef)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/57513ab5-2add-421b-883c-da3e7af59989)

Clique em `Create Self-Signed Certificate`, está do lado direito da janela:

![244530010-d18e7f91-120c-4025-908d-300c2c829858](https://github.com/wendersoon/WindowsServer/assets/104470835/5ef3e935-02a2-4502-8414-27c896d1b1c6)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/d18e7f91-120c-4025-908d-300c2c829858)

Será pedido apenas duas informações, o nome que deseja dá e o tipo de certificado:

![244530211-6fe253fd-7323-4f9b-809a-158746ae8ea7](https://github.com/wendersoon/WindowsServer/assets/104470835/20ffa251-6472-46d1-943d-5ceadda4e2b9)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/6fe253fd-7323-4f9b-809a-158746ae8ea7)

Após isso clique com o botão direito do mouse no seu site e vá em `Edit Bidings...`

![244531071-c573f14e-3923-4bb1-acd0-c9dd91090049](https://github.com/wendersoon/WindowsServer/assets/104470835/a9f17654-6632-4ad8-8348-64de4d822189)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c573f14e-3923-4bb1-acd0-c9dd91090049)

E adicione as seguintes configurações:

![244531407-a3b1b398-bf13-42e5-a055-ca93d70c66a0](https://github.com/wendersoon/WindowsServer/assets/104470835/f8dd8e4c-20e1-4734-a465-633e00544758)

![Screencast from 08-06-2023 20_13_02](https://github.com/wendersoon/WindowsServer/assets/104470835/a3b1b398-bf13-42e5-a055-ca93d70c66a0)

Reinicie o seu site, você vai achar essa função no lado direito do painel:

![244531572-5012d5cb-38fc-45fa-9ac3-e9c70df2e9d7](https://github.com/wendersoon/WindowsServer/assets/104470835/9550ee8d-bff3-48ed-91ec-937df225e230)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/5012d5cb-38fc-45fa-9ac3-e9c70df2e9d7)

Vejamos se funcionou, acessando o link `https://IP-DO-SERVIDOR`.

![244532123-bdab6fe6-326e-410d-acd6-ac9f9b946e21](https://github.com/wendersoon/WindowsServer/assets/104470835/3efa505d-13c8-4d77-8576-a139727a589a)

![Screencast from 08-06-2023 20_19_59](https://github.com/wendersoon/WindowsServer/assets/104470835/bdab6fe6-326e-410d-acd6-ac9f9b946e21)

Deu certo :)

## Extra: Servidor FTP

Para instalar a função de servidor FTP basta seguir os mesmos passos da instalação do IIS. Porque a função do FTP é entendido como uma extensão do próprio IIS, veja no print abaixo onde vamos marcar a função para poder instalar:

![244533271-c2b8baff-6c3b-42f4-86cd-c5b3fd3b2ae3](https://github.com/wendersoon/WindowsServer/assets/104470835/09ae5e9c-6679-4594-985f-79c1854d5383)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/c2b8baff-6c3b-42f4-86cd-c5b3fd3b2ae3)

Após isso acesse as configurações do ISS para o servidor e veja o roll de novas funções disponíveis:

![244534083-f2845ee0-d39f-440c-8409-e24ec4c983ae](https://github.com/wendersoon/WindowsServer/assets/104470835/1484ca99-78e4-4a6a-b162-6d938795e4ff)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/f2845ee0-d39f-440c-8409-e24ec4c983ae)

Para adicionar um servidor FTP, basta clicar em `Add FTP Site...`

![244537901-e2c9fec6-2f57-431a-9fa7-3c88b697b42b](https://github.com/wendersoon/WindowsServer/assets/104470835/ed717449-ab77-4248-8afc-ef24571faa34)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e2c9fec6-2f57-431a-9fa7-3c88b697b42b)

Na primeira janela adicione o nome do seu servidor FTP e escolha a pasta que irá ser compartilhada. 

![244540471-2f336319-ce4f-4847-9476-b6580d300a35](https://github.com/wendersoon/WindowsServer/assets/104470835/8775e023-3ece-4ebe-a5c8-4757acb452a6)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2f336319-ce4f-4847-9476-b6580d300a35)

Na próxima janela informe o IP e a porta, e marque a opção de não usar o certificado:

![244541007-8af1113d-e4d8-42a9-a490-c118f331d9b5](https://github.com/wendersoon/WindowsServer/assets/104470835/2cdd8d90-61b4-4a6a-95a4-3e68e4f540cc)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/8af1113d-e4d8-42a9-a490-c118f331d9b5)

E em seguida informe o/os usuários que irão utilizar e o que podem fazer. Lembre-se que aqui é apenas um tutorial, em um servidor de produção deve-se ter sempre o cuidado em compartilhar pastas na rede:

![244541230-9ef529c3-29c0-445b-9504-c095219d344b](https://github.com/wendersoon/WindowsServer/assets/104470835/7cf37b0b-31ea-4939-ac8d-9d38e73d4b82)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/9ef529c3-29c0-445b-9504-c095219d344b)

Pronto, nosso servidor já está funcionando!


Para acessá-lo basta que você abra o navegador Internet Explorer no seu servidor e busque na URL por `ftp:\\IP-DO-SERVIDOR`, será pedido as informações de login. Veja o print abaixo:

![244542652-ac6f963c-3578-409e-8ece-c1d1ab973eef](https://github.com/wendersoon/WindowsServer/assets/104470835/a7ee1bf4-ab89-4a37-bcf3-85cb8dfa835b)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ac6f963c-3578-409e-8ece-c1d1ab973eef)

---

Terminamos aqui nosso artigo. Obrigado pela leitura!





