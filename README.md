<h1>APP Força de Vendas :shopping_cart:</h1> 

<!-- <p align="center">
  <img src="https://www.jetbrains.com/guide/assets/csharp-logo-265a149e.svg"/>
  <img src="https://img.shields.io/static/v1?label=Netlify&message=deploy&color=blue&style=for-the-badge&logo=netlify"/>
  <img src="http://img.shields.io/static/v1?label=License&message=MIT&color=green&style=for-the-badge"/>
  <img src="http://img.shields.io/static/v1?label=Ruby&message=2.6.3&color=red&style=for-the-badge&logo=ruby"/>
  <img src="http://img.shields.io/static/v1?label=Ruby%20On%20Rails%20&message=6.0.2.2&color=red&style=for-the-badge&logo=ruby"/>
  <img src="http://img.shields.io/static/v1?label=TESTES&message=%3E100&color=GREEN&style=for-the-badge"/>
   <img src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=RED&style=for-the-badge"/>
   <img src="http://img.shields.io/static/v1?label=STATUS&message=CONCLUIDO&color=GREEN&style=for-the-badge"/>
</p> -->

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



## Funcionalidades

:heavy_check_mark: [Pedido](#pedido-shopping_cart)

:heavy_check_mark: [Cliente](#cliente-frowning_man)

:heavy_check_mark: [Consulta Pedidos](#Consulta-Pedidos-shopping_cart)

:heavy_check_mark: [Consulta Clientes](#Consulta-Clientes-busts_in_silhouette)

:heavy_check_mark: [Permissões](#Permissões-lock)

:heavy_check_mark: [Usuários](#Usuários-frowning_person)

:heavy_check_mark: [Offline](#Offline-signal_strength)


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

**1. Novo Pedido:**  

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



<!-- **protected override async Task OnInitializedAsync()**  

- Primeiro método que é carregado quando a pagina é aberta  
- Carrega todas as informações necessários para ser possivel efetuar um pedido:
Lista de Preço, Formas de pagamento, Vendedores, Dados do usuário logado, comissão variável. -->

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

**2. Index Pedido:**  

Pagina inicial dos pedidos, traz somente os pedidos feitos no aplicativo e o botão de novo pedido.  
Os pedidos que estiverem em rascunho podem ser editados, excluidos e gerado um relatório.  
Os pedidos que foram enviados, podem ser visualizados, replicadas e os que ja foram integrados é possivel gerar um pdf do pedido.

**3. Editar Pedido / Replicar Pedido**  

A maioria dos métodos são iguais a do Novo Pedido  

> Editar Pedido:  
> - A funcionalidade dessa pagina é poder editar somente os rascunhos.  

> Replicar Pedido:  
> - A funcionalidade dessa pagina é replicar pedidos enviados.  

**protected override async Task OnInitializedAsync()**  
> Esse método é o primeiro a ser carregado quando a pagina abre. Aqui fazemos a busca do pedido via API através do ID,  
depois fazemos a busca dos itens desse pedido. 
> - Os itens salvos no banco não possuem diversas informações necessárias para a visualização,  
então é feita uma busca na Lista de Preço, para pegar as informações que faltam.  
> - É montado todas as informações do pedido como dados de cliente, formas de pagamento e vendedores.  

## Cliente: :frowning_man:

Descrição do programa Cliente

## Consulta Pedidos: :shopping_cart:

Descrição do programa Consulta Pedidos

## Consulta Clientes: :busts_in_silhouette:

Descrição do programa Consulta Clientes

## Permissões: :lock:

Descrição do programa Permissões

## Usuários: :frowning_person:

Usuários serão cadastrados pelo time de infra-estrutura interno, e serão repassados os representantes.  

Existe um cadastro de Usuário Fake, sendo possivel cadastrar email, usuário e senha, somente para fins da loja Apple.

## Offline: :signal_strength:

Descrição das funcionalidades Offline

## Linguagens, dependencias e libs utilizadas :books:

Linguagens:
- Front End - [.Net Maui Blazor Hibrid](https://learn.microsoft.com/pt-br/aspnet/core/blazor/hybrid/tutorials/maui?view=aspnetcore-8.0)  
- Comunicação via API - [API RESTFUL](https://aws.amazon.com/pt/what-is/restful-api/)  
- BackEnd - [C#](https://learn.microsoft.com/pt-br/dotnet/csharp/)  

Bibliotecas:
- Notificações [OneSignal](https://documentation.onesignal.com/reference/quick-start-api-guide)
- Estilização/Componentes - [MudBlazor](https://mudblazor.com/docs/overview)
- Gerar PDF - (verificar Doc) [DinkToPdf](https://github.com/rdvojmoc/DinkToPdf)


## Licença 

The [MIT License]() (MIT)

Copyright :copyright: 2024 - Feltrin Sementes
