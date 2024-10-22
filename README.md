<h1>APP Força de Vendas :shopping_cart:</h1> 


> Status do Projeto: :heavy_check_mark: Em Andamento

### Tópicos 

:small_blue_diamond: [Descrição do projeto](#descrição-do-projeto-blue_book)

:small_blue_diamond: [Funcionalidades](#funcionalidades)

:small_blue_diamond: [Deploy da Aplicação](#layout-ou-deploy-da-aplicação)

:small_blue_diamond: [Pré-requisitos](#pré-requisitos)

:small_blue_diamond: [Como rodar a aplicação](#como-rodar-a-aplicação-arrow_forward)


## Descrição do projeto :blue_book:

<p align="justify">
  Este aplicativo de vendas é uma solução híbrida desenvolvida em .NET MAUI Blazor, projetada para atender às necessidades de representantes comerciais. Com ele, os representantes podem gerenciar eficientemente suas operações de vendas, permitindo o cadastro de clientes, realização de pedidos, geração de relatórios, consulta de informações de clientes e pedidos, além de acessar listas de preços atualizadas. O aplicativo oferece uma interface amigável e funcional, que pode ser utilizada tanto em dispositivos Android quanto IOS, podendo ser utilizado offline, proporcionando flexibilidade e praticidade para os profissionais de vendas no campo.
</p>

## Linguagens, dependencias e libs utilizadas :books:

Linguagens:
- Front End - [.Net Maui Blazor Hibrid](https://learn.microsoft.com/pt-br/aspnet/core/blazor/hybrid/tutorials/maui?view=aspnetcore-8.0)  
- Comunicação via API - [API RESTFUL](https://aws.amazon.com/pt/what-is/restful-api/)  
- BackEnd - [C#](https://learn.microsoft.com/pt-br/dotnet/csharp/)  

Bibliotecas:
- Notificações [OneSignal](https://documentation.onesignal.com/reference/quick-start-api-guide)
- Estilização/Componentes - [MudBlazor](https://mudblazor.com/docs/overview)
- Gerar PDF - (verificar Doc) [DinkToPdf](https://github.com/rdvojmoc/DinkToPdf)

## Funcionalidades

:heavy_check_mark: [Pedido](#pedido-shopping_cart)

:heavy_check_mark: [Cliente](#cliente-frowning_man)

:heavy_check_mark: [Consulta Pedidos](#Consulta-Pedidos-shopping_cart)

:heavy_check_mark: [Consulta Clientes](#Consulta-Clientes-busts_in_silhouette)

:heavy_check_mark: [Permissões](#Permissões-lock)

:heavy_check_mark: [Usuários](#Usuários-frowning_person)

:heavy_check_mark: [Offline](#Offline-signal_strength)

:heavy_check_mark: [Home](#Home-house)

:heavy_check_mark: [MainLayout](#MainLayout-houses)


## Layout ou Deploy da Aplicação

> Link do Layout da aplicação. [Pedido](https://app.uizard.io/p/f6f2e7e8)  
> Link do Layout da aplicação. [Itens](https://app.uizard.io/p/2c6017c9)   

> Link do deploy da aplicação. [Google Play](https://play.google.com/store/games?hl=pt_BR&pli=1)  
> Link do deploy da aplicação. [APP Store](https://www.apple.com/br/app-store/)



## Pré-requisitos

:warning: [Visual Studio 2022](https://visualstudio.microsoft.com/pt-br/)  
:warning: [Pacote Desenvolvimento de .NET Multi-Plataform App UI](https://learn.microsoft.com/pt-br/dotnet/communitytoolkit/maui/get-started?tabs=CommunityToolkitMaui) (Baixar no Visual Studio)  
:warning: [Android Device Manager](https://learn.microsoft.com/pt-br/dotnet/maui/android/emulator/device-manager?view=net-maui-8.0)  
:warning: [SQL Server Management Studio](https://learn.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver16)  


## Como rodar a aplicação :arrow_forward:

Primeiro é necessário clonar a aplicação:

    Abra o Visual Studio e clique em Clonar um repositório,  
    selecione Azure DevOps e depois clique em FeltrinAppWinnersV2_2  
    após isso clique em Conectar e assim o repositório será clonado.  

Passo a passo para rodar a aplicação dentro do simulador android. :iphone:  

    Ao lado do botão de Iniciar selecione Estrutura e net8.0-android  
    é necessário para funcionar dentro do simulador, mudar a url base da API  
    pois como está em debug, tentará usar o localHost, que não sera encontrado dentro do simulador

## Pedido: :shopping_cart:
<!-- **Descrição:**
A funcionalidade de pedido permite que os representantes comerciais realizem os pedidos dos clientes de forma rápida e eficiente.   -->

**1. Index Pedido:**  

Pagina inicial dos pedidos, traz somente os pedidos feitos no aplicativo e o botão de novo pedido.  
> - Os pedidos que estiverem em rascunho podem ser editados, excluidos e gerado um relatório.  
> - Os pedidos que foram enviados, podem ser visualizados, replicadas e os que ja foram integrados é possivel gerar um pdf do pedido.

**2. Novo Pedido:**  

A funcionalidade de Novo Pedido permite que os representantes comerciais realizem os pedidos dos clientes de forma rápida e eficiente.  

__Como funciona:__

> 1. O representante seleciona o cliente na lista de clientes cadastrados. (Obrigatório)
> 2. A seguir, escolhe os produtos desejados, inserindo a quantidade. (Obrigatório)
> 3. O representante que possuir comissão variável pode aumentar o valor dos itens.
> 4. O sistema calcula automaticamente o valor total do pedido com base na lista de preços atualizada.
> 5. Selecionar forma de pagamento (Obrigatório)
> 6. Adicionar Comentários (Opcional)
> 7. Selecionar Segundo Vendedor (Opcional)
> 8. O pedido pode ser salvo como rascunho, ou finalizado.
> 9. Após a finalização, o representante pode gerar um relatório detalhado do pedido ou enviá-lo por e-mail para o cliente.


**private void AdicionarAoCarrinho(vwListaDePreco item, decimal quantidade)**  
> - Primeiro é valido se esse item já está no pedido, se estiver, a quantidade é atualizada e o preço total também,  
se não estiver, o item é adicionado ao pedido.  
> - Depois é feito uma validação na quantidade, para ver se ela é multipla do seu multiplicador,  
por exemplo um produto que é vendido em pacotes de 250 gramas, não é possivel adicionar 400 gramas.  
> - Por ultimo o item é adicionado a lista Produtos

**private void AlteraPrecoTotal(Produto prod)**  

> Esse método serve para quando um item que já esta na lista, é alterado seu valor ou quantidade.  
> - É feito diversas validações: Preço Negociavel não pode ser menor que o preço original (somente se preço com desconto não existir)  
> - Se o Preço for alterado e o item for de uma grade, a lista de produtos é percorrida atualizando o valor de todos os itens dessa grade.  
> - Se quantidade igual a 0 o item é removido da lista  
> - A validação se a quantidade é multipla do multiplicador do item.  
> - Altera o preço total do item e o preço total do pedido.

**private async void SalvarPedido(int situacao)**  

> Esse método monta o pedido com todas as informações  
> - É criado uma projeção de Pedido
> - A Lista de produtos é adicionada a projeção
> - É adicionado todos os dados, referente a cliente, forma de pagamento, comentário, vendedores, etc...  


**3. Editar Pedido / Replicar Pedido / Visualizar Pedido**  

A maioria dos métodos são iguais a do Novo Pedido  

> Editar Pedido:  
> - A funcionalidade dessa pagina é poder editar somente os rascunhos.  

> Replicar Pedido:  
> - A funcionalidade dessa pagina é replicar pedidos enviados.  

> Visualizar Pedido
> - A funcionalidade dessa pagina é somente visualizar os pedidos já enviados.

**protected override async Task OnInitializedAsync()**  
> Esse método é o primeiro a ser carregado quando a pagina abre. Aqui fazemos a busca do pedido via API através do ID,  
depois fazemos a busca dos itens desse pedido. 
> - Os itens salvos no banco não possuem diversas informações necessárias para a visualização,  
então é feita uma busca na Lista de Preço, para pegar as informações que faltam.  
> - É montado todas as informações do pedido como dados de cliente, formas de pagamento e vendedores.  

## Cliente: :frowning_man:

**1. Index Cliente**  

Essa pagina traz a lista de cliente que foram cadastrados pelo aplicativo.  

> - É possivel visualizar os clientes cadastrados.  
> - É possivel cadastrar novos clientes.  
> - Não é possivel editar ou excluir um cliente.  

**2. Novo Cliente**  

Nessa página possivel fazer o cadastro de novos clientes.  

__Como funciona:__

> 1. O representante seleciona o tipo de cliente (Físico ou jurídico). (Obrigatório)
> 2. A seguir, digita o CPF ou CNPJ. (Obrigatório)
> 3. É necessário preencher todos os campos que possuem (*) ao lado do nome. (Obrigatório)
> 4. Para pessoa Juridica quando o CNPJ e estado forem preenchidos será feita uma busca e preencherá os campos. (Obrigatório)  


**private async Task BuscaCadastroCliente()**  
> - É feito a validação se o CPF ou CNPJ são validos
> - É validado se esse clientes já existe (evitar duplicatas) 

## Consulta Pedidos: :shopping_cart:

**1. Consulta Pedidos**  

Nessa página é possivel todos os pedidos de uma região que já estão no winners.  

__Funcionalidade:__

> 1. O representante seleciona os meses que ele quer ver os pedidos. (Opcional)
> 2. Pode ser feita a busca de pedidos, bucando por Cliente, CPF, CNPJ, Numero do Pedido. (Opcional)
> 3. Ao clicar em um pedido será mostrada todas as informações detalhados do pedido. (Opcional)

**2. Visualizar Consulta Pedidos**  

Essa pagina traz informações detalhadas do pedido selecionado. 

__Funcionalidade:__

> 1. Replicar o pedido, será replicado itens, forma de pagamento, cliente, comentários, vendedor.  
 Valor negociavel dos itens NÃO SERÁ REPLICADO ( ficará com o valor original).  
> 2. É possivel efetuar o download do resumo do pedido.
> 3. Clicando no nome do Cliente, será redirecionado para as informações detalhadas do cliente.

**private async void Replicar(long id)**
> Esse método é executado se for selecionada a opção Replicar Pedido.
> - A verificado se todos os itens ainda possuem estoque para poderem ser replicados,  
em caso de itens em falta, é mostrado uma mensagem com os itens que não possuem estoque.

**3. Replicar Consulta Pedidos**  

Essa pagina replica o pedido selecionado. (Pedido que vem do winners) 

__Como funciona:__

> 1. Todas as informaçãoes do pedido já vem preenchidas de acordo com o pedido selecionado.  
> 2. Valor Negociavel NÃO É REPLICADO, produto vem com o valor original 


## Consulta Clientes: :busts_in_silhouette:

**1. Consultar Clientes**  

Essa pagina traz todos os clientes do winners de acordo com a região do usuário logado. 

__Funcionalidade:__

> 1. Se a região tiver filhos, é possível filtar por região  
> 2. É possivel fazer a busca de um cliente por Nome, CPF e CNPJ.
> 3. Clicando no Cliente, será redirecionado para as informações detalhadas do cliente.

**2. Ver Mais Cliente**  

Essa pagina traz informações detalhadas sobre o cliente selecionado e seus pedidos. 

__Funcionalidade:__

> 1. Clicando no endereço será redirecionado para o google maps mostrando a localização.  
> 2. Se ele possuir pedidos em andamento, trará uma lista com todos os pedidos em andamento e seus respectivos status.
> 3. No final da pagina existe uma lista com os 10 ultimos pedidos, sendo possivel clicar e visualizá-lo.

## Usuários: :frowning_person:

Usuários serão cadastrados pelo time de infra-estrutura interno, e serão repassados os representantes.  
Cada usuário pode pertencer a diversos grupos de permissão.  
Existe um cadastro de Usuário Fake, sendo possivel cadastrar email, usuário e senha, somente para fins da loja Apple.

## Grupos de Permissão: :lock:

Grupos de permissão serão criados pelo time de infra-estrutura interno, a cada grupo terá acesso aos programos necessários.

## Offline: :signal_strength:

Certas funcionalidades do APP precisam funcionar Offline, são elas: Pedido, Cliente, Lista De Preço.

**public async Task SalvarArquivo(string arquivoNome, List<T> pedidos)**

Esse método serve para salvar um lista de objetos em um arquivo na memória do celular que pode ser acessado offline.
> 1. Primeiro ele monta o caminho do arquivo.
> 2. Depois serializa o a lista de objetos.
> 3. E por fim salva a lista serializada no caminho arquivo criado.

**public async Task<List<T>?> RetornarPedidosNaoIntegrados<T>(string arquivoNome)**

Esse método retorna a Lista de objetos de um arquivo salvo na memória do celular
> 1. Primeiro ele monta o caminho do arquivo.
> 2. Depois ele le esse arquivo e deserializa.
> 3. E por retorna a lista de objetos.

## Home: :house:

Essa é a tela inicial, possuem duas homes, uma para quando está logado e a outra não.  

__Funcionalidade Logado:__

> 1. Existem dois atalhos, Novo Cliente e Novo Pedido.  
> 2. Componente de Meta do representante, podendo selecionar o quadrimestre do ano e ver sua meta.

__Funcionalidade Deslogado:__

> 1. Carrosel de imagens com os produtos da Feltrin.  
> 2. Links para redes sociais e site.

## MainLayout: :houses:

MainLayout é o Layout padrão de todas as paginas, aqui está o Menu, Header, Botões do Login e estilização geral do APP.  

**protected override async Task OnInitializedAsync()**  

Esse método serão inicializadas todas as informações necessários para o APP funcionar. 
> 1. Primeiro é verificado se possui Token, se possuir é verificado sua validade.
> 2. Se estiver logado é enviado os Pedidos e Clientes pendentes, que foram cadastrados offline.
> 3. É feita todas as chamadas assincronas para as informações ja irem carregando. 

**public async Task FiltrarMenuItems()**

Esse método declara e faz toda a lógica do menu.
> 1. Primeiro é feito a busca de permissões e salva em um arquivo para funcionar offline.
> 2. Depois é declarado todo o menu.
> 3. E por ultimo é filtrado para aparecer somente os programas que o usuário possui permissão. 

**private async Task<string> Notificacao()**

Esse método é chamado quando eu feito Login
> 1. Registra a região do usuário logado no usuário do OneSignal,  
para esse usuário receber somente as notificações referentes a sua região.  

**private async Task<string> NotificacaoDesvincular()**

Esse método é chamado quando é feito o logout ou o tempo de validade do token expira
> 1. Desvincula a região ao usuário do oneSignal. 

**private async void HandleLocationChanged(object sender, LocationChangedEventArgs args)**

Sempre que a é modifica esse método é chamado
> 1. É feita a validação do token, se ele existe e se a validade não expirou.
> 2. Se o token não for mais válido ou não existir o usuário é deslogado 




## Licença 

The [MIT License]() (MIT)

Copyright :copyright: 2024 - Feltrin Sementes




