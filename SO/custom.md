# Configurações Iniciais

Veremos nesse tópico as configurações que são desejáveis quando iniciamos um servidor Windows, por exemplo, trocar o nome do servidor, colocar IP fixo etc.


### Alterando o nome do servidor

O primeiro passo é abrir o **Server Manager** que está localizado no menu iniciar:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/944b9116-10c2-45af-96a6-97938da5b62d)

Em seguida vamos alterar o nome do nosso servidor e para iso vá em **Local Server** --> clique no nome do servidor logo a frente de **Computer Name** --> clique em **change**. Altere o nome e clique ok, assim que o servidor reiniciar já estará com o nome alterado. Veja o gif abaixo:

![Screencast from 29-05-2023 17_32_16](https://github.com/wendersoon/WindowsServer/assets/104470835/0eb3ea4e-b04a-45dd-991e-ca700a35c619)

### Adicionando IP estático no servidor

Em geral, toda configuração de servidor deve ter essa etapa que é a determinação de um IP estático por causa de seus serviçoes dedicados e mais ainda para facilitar uma manutenção futura. Para alteramos o IP (OBS: ainda em **Local Server**) siga os seguintes passos: clique em **IPv4 Adress assigned by DHCP, IPv6 enabled** --> Vá nas **propriedades** da placa de rede --> Procure **Internet Protocol IPv4 (TCP/IPv4)** e clique --> Clique em **Properties** e adicione as configurações da sua rede. Lembrando que aqui não usaremos IPv6, então por isso desmarco essa opção. Veja as imagens abaixo:

* Local da Configuração:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/1b214567-f3a0-4889-8f40-bbe8460a54a3)

* Caminho para alterar o IP:

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/8635c69b-00a2-43b5-970a-7039c90f6451)

### Atualizando o servidor

Uma das coisas mais importantes de um servidor é mantê-lo atualizado pois isso garante uma maior segurança ao sistema como um todo. Para atualizar nosso servidor siga os seguintes passo: na lupa ao lado do menu iniciar pesquise por **Windows Update** --> clique em **Check for Updates** --> clique em **Install Now**. É importante uma observação, se você ao configurar a máquina virtual não alocou muito espaço em disco, fazer essa atualização pode dar problemas de espaço para o seu servidor.

* Pesquisa por **Windows Update**

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/2b3dc2b3-dc3d-483d-83fb-77adb786ac04)

* Instalação das atualizações

![image](https://github.com/wendersoon/WindowsServer/assets/104470835/4fe93220-8f28-432f-abb1-1106ba9250f0)

Depois de atualizado, reinicie o servidor.

### Ativando o Windows Defender


