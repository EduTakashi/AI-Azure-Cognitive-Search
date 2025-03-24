# AI-Azure-Cognitive-Search
 Azure Cognitive Search: Utilizando AI Search para indexação e consulta de Dados
 
----------------------------------------------------------------------------------

## Aprendizado 

O Azure AI Search é uma daquelas ferramentas que realmente fazem a diferença quando o assunto é buscar e organizar informações de forma inteligente. Ele pode ser um grande aliado em várias situações, seja para tornar a busca em um e-commerce mais intuitiva, ajudar um chatbot a responder perguntas com mais precisão ou até facilitar a pesquisa em grandes bases de documentos dentro de uma empresa. No fim das contas, qualquer sistema que lide com muitos dados pode se beneficiar dessa tecnologia para oferecer resultados mais rápidos e relevantes.

Durante a implementação, algumas lições ficam bem claras. A primeira é que a organização dos dados faz toda a diferença. Se os documentos e informações estiverem bem estruturados, a busca se torna muito mais eficiente. Outra coisa importante é explorar os enriquecimentos cognitivos, que permitem ir além da busca tradicional, trazendo funcionalidades como reconhecimento de imagens, extração de texto de documentos digitalizados e até análise de entidades dentro dos conteúdos.

Testes também são essenciais. Pequenos ajustes no peso dos campos ou na configuração do índice podem impactar bastante a qualidade dos resultados. E claro, não adianta ter um sistema super inteligente se a experiência do usuário for confusa. A forma como os resultados são apresentados precisa ser clara e intuitiva para que as pessoas realmente encontrem o que estão procurando sem esforço.

No fim das contas, o Azure AI Search não é só um mecanismo de busca, mas uma ferramenta que pode transformar a maneira como lidamos com a informação. Implementá-lo é um processo cheio de aprendizado, onde cada ajuste traz novos insights. E quanto mais refinamos a busca, mais ela trabalha a nosso favor, garantindo que as informações certas apareçam no momento certo.

---------------------------------------------------------------------------------------------

## Prints dos processos 

### Implementação da conta de armazenamento 

![image](https://github.com/user-attachments/assets/29fe6355-8af5-4f10-9d18-3a5556753a8c)

----------------------------------------------------------------------------------------

### Criação do container

Container criado após a configuração Permitir acesso anônimo ao Blob ser habilitada
Container criado com a opção Contêiner (acesso de leitura anônimo para contêineres e blobs)

![image](https://github.com/user-attachments/assets/e486f5f1-13bf-4cf2-a5dd-5132eb1f6aca)

-------------------------------------------------------------------------------------------

Depois de armazenar os documentos, você poderá utilizar o Azure AI Search para obter insights valiosos a partir deles. O portal do Azure oferece um assistente de importação de dados que facilita esse processo. Com essa ferramenta, é possível criar automaticamente um índice e um indexador para fontes de dados compatíveis. Você usará o assistente para configurar um índice e importar seus documentos do armazenamento para o índice do Azure AI Search.

--------------------------------------------------------------------------------------------

### Conectando-se aos seus dados

Na página Conectar-se aos seus dados, vá até a lista Fonte de Dados e selecione Armazenamento de Blobs do Azure. Depois, preencha os detalhes com as seguintes informações:

- Fonte de dados: Armazenamento de Blobs do Azure
- Nome da fonte de dados: coffee-customer-data
- Dados a extrair: Conteúdo e metadados
- Modo de análise: Padrão
- Cadeia de conexão: Escolha uma conexão existente, selecione sua conta de armazenamento e o contêiner de avaliações de café, depois clique em Selecionar.
- Autenticação de identidade gerenciada: Nenhuma
- Nome do contêiner: Esse campo será preenchido automaticamente após escolher a conexão.
- Pasta Blob: Deixe em branco.
- Descrição: Avaliações sobre Fourth Coffee Shops

-------------------------------------------------------------------------------------------------------------------------------------------------------

### Configurando os Serviços Cognitivos
Na seção Anexar Serviços Cognitivos, selecione o seu recurso de Serviços Azure AI.
Adicionando enriquecimentos
Renomeie a Skillset para coffee-skillset.
Marque a opção Habilitar OCR e mesclar todo o texto no campo merged_content.
Dados de origem: Deve estar definido como merged_content.
Nível de granularidade do enriquecimento: Defina para Páginas (blocos de 5.000 caracteres).
Não selecione Habilitar enriquecimento incremental.
Escolha os campos enriquecidos conforme a documentação.

-----------------------------------------------------------------------------------------------------------------------------------------------------------

### Criando o índice

Nome do índice: índice de café
Chave: Defina como metadata_storage_path.
Nome do sugeridor: Deixe em branco.
Modo de pesquisa: Preenchido automaticamente.
Revise as configurações padrão dos campos do índice e marque "filtrável" para todos os campos que já estão selecionados por padrão.
Clique em Próximo: Criar um indexador.

----------------------------------------------------------------------------------------------------------------------------------------------------------------

### Consultando o índice

Você pode usar o Search Explorer para testar suas consultas e verificar se o índice está funcionando corretamente.
Na Visão geral do serviço de pesquisa, clique em Explorador de pesquisa no topo da tela.
O índice selecionado deve ser o índice de café que você criou.
Abaixo do índice selecionado, altere a visualização para JSON para ver os resultados estruturados.
