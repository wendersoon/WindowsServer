![241810854-0f79ef7a-e227-4267-8f3c-f94cdc66facc](https://github.com/wendersoon/WindowsServer/assets/104470835/498341d0-e249-4660-95a9-911b98cd39b3)# Configurações Iniciais

Veremos nesse tópico as configurações que são desejáveis quando iniciamos um servidor Windows, por exemplo, trocar o nome do servidor, colocar IP fixo etc.


### Alterando o nome do servidor

O primeiro passo é abrir o **Server Manager** que está localizado no menu iniciar:

![241581458-944b9116-10c2-45af-96a6-97938da5b62d](https://github.com/wendersoon/WindowsServer/assets/104470835/3859d617-8478-4fd6-9d3f-2db556b59aa9)

Em seguida vamos alterar o nome do nosso servidor e para iso vá em **Local Server** --> clique no nome do servidor logo a frente de **Computer Name** --> clique em **change**. Altere o nome e clique ok, assim que o servidor reiniciar já estará com o nome alterado. Veja o gif abaixo:

![241803566-0eb3ea4e-b04a-45dd-991e-ca700a35c619](https://github.com/wendersoon/WindowsServer/assets/104470835/e1c982ff-3aa6-4c2d-b2a6-723fb3537f22)

### Adicionando IP estático no servidor

Em geral, toda configuração de servidor deve ter essa etapa que é a determinação de um IP estático por causa de seus serviçoes dedicados e mais ainda para facilitar uma manutenção futura. Para alteramos o IP (OBS: ainda em **Local Server**) siga os seguintes passos: clique em **IPv4 Adress assigned by DHCP, IPv6 enabled** --> Vá nas **propriedades** da placa de rede --> Procure **Internet Protocol IPv4 (TCP/IPv4)** e clique --> Clique em **Properties** e adicione as configurações da sua rede. Lembrando que aqui não usaremos IPv6, então por isso desmarco essa opção. Veja as imagens abaixo:

* Local da Configuração:

![241805754-1b214567-f3a0-4889-8f40-bbe8460a54a3](https://github.com/wendersoon/WindowsServer/assets/104470835/3fa1d9f5-fa61-4c6e-84e7-d58c5a125a7d)

* Caminho para alterar o IP:

Perceba que defini um IP estático e também defini como DNS primário o próprio IP da máquina para que ela seja cliente dela mesmo e assim a infraestrutura esteja fechado, essa configuração nos será muito nos próximos artigos!

![244942053-17c6b251-c053-40d6-aafd-7c24e4f0af04](https://github.com/wendersoon/WindowsServer/assets/104470835/4d94a7af-a6e1-4c93-bc32-d7a650b6500b)

### Atualizando o servidor

Uma das coisas mais importantes de um servidor é mantê-lo atualizado pois isso garante uma maior segurança ao sistema como um todo. Para atualizar nosso servidor siga os seguintes passo: na lupa ao lado do menu iniciar pesquise por **Windows Update** --> clique em **Check for Updates** --> clique em **Install Now**. É importante uma observação, se você ao configurar a máquina virtual não alocou muito espaço em disco, fazer essa atualização pode dar problemas de espaço para o seu servidor.

* Pesquisa por **Windows Update**

![241808457-2b3dc2b3-dc3d-483d-83fb-77adb786ac04](https://github.com/wendersoon/WindowsServer/assets/104470835/d7602066-ae66-4fa2-83e1-4cf801ad217c)

* Instalação das atualizações

![241808235-4fe93220-8f28-432f-abb1-1106ba9250f0](https://github.com/wendersoon/WindowsServer/assets/104470835/c76992bd-e4ee-428a-981f-5b44938a1957)

Depois de atualizado, reinicie o servidor.

### Verificar o Windows Defender

Após a atualização, vamos verificar se está tudo ok com o **Windows Defender**. Para isso basta que pesquisemos na lupa por **Windows Defender**, acesse e lá teremos a seguinte janela:

![241810854-0f79ef7a-e227-4267-8f3c-f94cdc66facc](https://github.com/wendersoon/WindowsServer/assets/104470835/2f71ba02-daff-4f16-b0e3-52ce3433fd97)

Se estiver como essa tela, significa que está tudo ok. Se não, basta acessar o menu **Settings** no canto superior direito e ativar todas as opções.

---

Terminamos por aqui essa parte do projeto, até o próximo tópico!









