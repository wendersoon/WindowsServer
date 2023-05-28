# Instalação e Configuração

Usaremos como sistema operacional do nosso servidor o Windows Server 2016, iremos baixá-lo no site oficial da Microsoft atráves do [link](https://www.microsoft.com/pt-br/evalcenter/download-windows-server-2016). Você pode escolher a versão com a lingua que desejar, mas usaremos aqui a versão inglês:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/5def898c-d1f8-4c05-815b-a366f08d6bea)

Instalaremos a ISO no software de virtualização Oracle VM VirtualBox versão 7.0.4.. Segue os passos de instalação e configuração:

1. Configuração da máquina virtual: você vai em novo e adiciona as informações do nome, a pasta que deseja instalar e a imagem ISO e em seguida clica em *Próximo*. Se caso não aparece essa opção *novo*, você pode encontrá-la na guia *Máquina*. Temos também duas formas de fazer a instalação, isto é, temos a opção de instalação assistida e desassistida, aqui optei pela primeira opção porque nos testes que realizei a segunda opção sempre apresentava um erro.
 
![226125983-5cf21a60-f345-4738-a69b-28cec4dc775d](https://github.com/wendersoon/WindowsServer/assets/104470835/350f0aab-9248-494d-ad37-d73954c7fc65)

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/fbec5e60-a475-44cd-ad9f-ccd35f7eb287)

2. Deixe a próxima janela do jeito que está e clique em *próximo*:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2d75aa98-6a55-4e0c-9430-99959832d775)

3. Selecione a quantidade de núcleos do processador e de RAM que irá ficar disponível para a máquina virtual, é recomendado não ultrapassar a metade de RAM disponivel na sua máquina real. No meu caso colocarei 4GB e 1 núcleo do processador.

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/a56a9c4d-efff-4c01-98ed-8358b47bc81f)

4. Em seguida, selecione a quantide de espaço em disco que você quer alocar. No meu caso optei por 35GB de espaço que meu servidor terá disponível:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/e2d12023-4db7-4736-87dc-a0c57ed601f1)

Após isso irá aparecer um sumário de todas as configurações selecionadas, verifique se está tudo certo e clique em *finalizar*. Aguarde um pouco e Inicie a Máquina Virtual.

5. A primeira janela que irá aparecer é conforme a da imagem abaixo, selecione a linguagem(apesar de já ter baixado com a linguagem definida no site), o formato da hora e o tipo de teclado, por fim clique em *next*. Após isso irá aparcer a opção *Install Now*, clique nela:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2d6c4aa3-f101-45f3-9832-174ebc68acec)
 
6. Seleciona a edição **Windows Server 2016 Standard Evaluation(Desktop Experience)** o qual iremos trabalhar nesse projeto:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/0bc56e7a-e6f4-4e1d-bf6d-342bddc6dc98)

7. Na próxima janela aceite os termos de uso e clique em *next*. E em seguida, selecione a segunda opção onde começa com *"Custom: Install Windows ..."*:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/60ec171a-f34f-474f-9228-d4c8ca71f014)

8. Aguarde o processo de instalação ser concluído:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/ab93f76a-26b6-4230-8423-bb81a0fa6031)

No próximo tópico iremos ver algumas configurações iniciais para começar a trabalhar com o nosso servidor Windows.

Até mais!
