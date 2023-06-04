# Servidor WEB

<div align = "center">

![iis-logo-blue](https://github.com/wendersoon/WindowsServer/assets/104470835/30ac9ec0-faca-4980-8ae4-60f8d5d78392)

 </div>


Nesse artigo instalaremos o utilitário que permite termos um servidor web ativo. Esse utilitário é chamado no windows de **IIS (Internet Information Services)** que é um conjunto de serviços de servidor web fornecido pela Microsoft, ele também permite hospedar sites e aplicativos na web, oferecendo recursos avançados de segurança, gerenciamento e desempenho, além de, oferecer suporte a vários protocolos e serviços da web, como HTTP, HTTPS, FTP, FTPS, SMTP e NNTP. Ele é uma escolha popular entre os desenvolvedores que trabalham com a plataforma do Windows. Se você quiser saber mais sobre essa ferramenta, acesse o site oficial nesse [link](https://www.iis.net/). 

## Instalação

Para instalar o ISS ou qualquer outro serviço deve-se seguir os seguintes passos:

1. Ir em `Manage -> Add Rules and Features`. Se é a primeira vez que você abre essa janela irá aparecer uma janela chamada de "Before you begin" que é apenas uma janela informativa, você pode marcar a caixa de skip logo abaixo para pular sempre que abrir novamente esse menu e é isso que faremos. 

*OBS: Para não tornar-se repetitivo, toda vez que concluirmos uma configuração numa janela estará subentendido que clicamos em `next`, a não ser que eu cite outro botão.*

2. Na janela seguinte ("Instalation Type") é pedido basicamente duas coisas, se você que fazer a instalação em um servidor remoto ou local. No nosso caso é no servidor local então deixamos marcado a seguinte opção:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/81b5dbf2-e801-4ae9-bf3c-53dbbb12b8df)

3. Na próxima janela ("Server Selection") é onde selecionamos nosso servidor (sim kkkk), como tenho apenas um servidor ativo é só ele que irá aparecer.
4. A janela seguinte do assistente é onde de fato adicionamos o serviço/função que desejo instalar. Nela estão listadas muitos serviços, procuraremos por `Web Server (ISS)` como na imagem abaixo:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/eb4bf52b-639b-4d19-bb44-76c9ab11cdc8)

Se você observar, no lado direito irá sempre aparecer uma breve descrição daquilo que selecionamos. Ao marcar a caixa de diálogo do lado do serviço irá aparecer uma pequena janela pedindo para adicionar requisitos obrigatórios para que o serviço funcione corretamente e é isso que queremos, então bastar clicar em `Add Features`.

5. 

