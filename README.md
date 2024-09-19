# "Criando um Assistente de Delivery com AWS Step Functions e Bedrock"

O desafio tem como objetivo criar uma simulação de um sistema inteligente para sugerir um menu de delivery, utilizando Step Functions para controlar o fluxo de trabalho e Bedrock para gerar as respostas inteligentes. É uma forma prática de entender como os serviços AWS podem ser integrados para criar assistentes que automatizam tarefas e usam IA para oferecer uma experiência mais dinâmica e personalizada.

## Esclarecimentos

1. **Criando um Assistente de Delivery:**

        O termo "assistente de delivery" sugere que o objetivo do desafio é criar um sistema que ajude a organizar ou gerenciar um processo de entrega. Isso pode envolver gerar sugestões de itens como comida, bebida, ou local de entrega, algo muito comum em serviços de delivery (como iFood, Uber Eats, etc.). O assistente, neste caso, é provavelmente um conjunto de funções que automatizam essas sugestões com base em entradas do usuário ou parâmetros predefinidos.

2. **com AWS Step Functions:**

        O AWS Step Functions é um serviço que permite orquestrar fluxos de trabalho em que várias tarefas são executadas de maneira sequencial ou paralela. No contexto desse desafio, o Step Functions está sendo utilizado para coordenar diferentes processos (como sugerir comida, bebida e local). Cada um desses processos pode ser uma função Lambda separada, que é invocada em etapas específicas do fluxo de trabalho.

3. **e Bedrock:**

        O AWS Bedrock é uma plataforma que facilita o uso de modelos de IA generativa de grandes linguagens (como GPT ou Anthropic Claude). Nesse caso, ele provavelmente está sendo utilizado para gerar as sugestões com base em prompts (por exemplo, "sugira um prato de comida" ou "sugira uma bebida"). Bedrock ajuda a integrar inteligência artificial em seu fluxo de trabalho, gerando respostas automáticas e contextuais.

## Objetivo do Desafio

O objetivo do desafio é criar um fluxo de trabalho orquestrado que utilize:

- Step Functions para coordenar diferentes tarefas, como:
  - Obter sugestões de comida.
  - Obter sugestões de bebida.
  - Obter uma sugestão de localização.
  - Compilar essas sugestões em um menu completo.

- Bedrock para gerar essas sugestões com modelos de IA que respondem aos prompts. Ou seja, o Bedrock está sendo utilizado para "pensar" como um assistente virtual de delivery.

## Na Prática - Tecnologias e Linguagens

Para colocar esse projeto de um Assistente de Delivery com AWS Step Functions e Bedrock em prática, você precisaria de uma combinação de tecnologias e linguagens que permitam tanto a orquestração de fluxos de trabalho quanto a implementação das funções Lambda e integração com serviços de IA. Principais ferramentas e linguagens.

1. AWS Step Functions

    - **Função:** Orquestrar o fluxo de trabalho que executa diferentes tarefas em sequência ou paralelamente.
    - **Tecnologia:** AWS Step Functions.
    - **Configuração:** Os fluxos de trabalho são configurados usando JSON (código abaixo). Esse JSON define como cada tarefa será executada, qual será o próximo estado, e como os dados serão transmitidos entre as etapas.

2. AWS Lambda

- **Função:** Executar as funções de backend para gerar sugestões (como comida, bebida, localização).

- **Linguagens:** Você pode desenvolver as funções Lambda usando várias linguagens, dependendo de sua familiaridade e os requisitos do projeto:

  - **Node.js (JavaScript):** Muito popular para criar funções Lambda devido à sua leveza e suporte nativo na AWS.
  - **Python:** Outra linguagem amplamente usada para AWS Lambda, especialmente para manipulação de dados e integração com APIs externas.
  - **Go, Java, e C#** também são suportadas, mas geralmente são mais usadas em projetos específicos.

- **Configuração:** Cada função Lambda é implementada em um desses idiomas e depois implantada na AWS para ser chamada pelo Step Functions.

3. AWS Bedrock

- **Função:** Utilizar modelos de IA para gerar sugestões inteligentes de comida, bebida e localização.
- **Tecnologia:** AWS Bedrock.
- **API de integração:** Para invocar os modelos de IA do Bedrock, você precisaria fazer chamadas de API. Essas chamadas podem ser feitas diretamente a partir das funções Lambda que você implementa.
- **Linguagem:** A comunicação com o Bedrock se daria via requisições HTTP usando JSON como payload, por exemplo, em Node.js ou Python.

4. Banco de Dados (opcional)

- **Função:** Se você quiser armazenar dados do usuário, histórico de sugestões, ou registros de pedidos.

- **Tecnologia:**

  - **AWS DynamoDB:** Um banco de dados NoSQL altamente escalável da AWS que é fácil de integrar com Lambda.
  - **RDS (Relational Database Service):** Para um banco de dados relacional como MySQL ou PostgreSQL.

- **Linguagem:** A escolha do banco de dados dependerá da complexidade do projeto. Se o objetivo for simples, um banco NoSQL como DynamoDB pode ser mais fácil de integrar.

5. Frontend (opcional)

- **Função:** Se você quiser criar uma interface para que os usuários possam interagir com o assistente de delivery.

- **Tecnologias:**

        React.js: Popular para criar interfaces dinâmicas de usuário.
        Vue.js ou Angular: Alternativas para React.

- **Comunicação:** O frontend se comunicaria com suas funções Lambda usando APIs (AWS API Gateway).

6. Autenticação e Autorização (opcional)

- **Função:** Se você precisar controlar o acesso ao sistema (por exemplo, logins de usuários).

- **Tecnologia:**

        AWS Cognito: Um serviço de autenticação e autorização que permite integrar logins de usuários e gerenciar permissões.

- **Linguagem:** O Cognito pode ser configurado usando a interface AWS e integrado ao backend via chamadas API ou SDK.

7. Deploy e Gerenciamento de Infraestrutura

- **Terraform ou AWS CloudFormation:** Para gerenciar a infraestrutura como código, permitindo que você defina toda a infraestrutura AWS (Step Functions, Lambda, API Gateway, etc.) de forma automatizada.
- **AWS SAM (Serverless Application Model):** Uma ferramenta específica da AWS para simplificar a implantação de funções Lambda e APIs.
- **Docker (opcional):** Se você preferir empacotar suas funções Lambda com bibliotecas específicas, pode usar Docker para criar imagens customizadas.

8. API Gateway

- **Função:** Se você deseja expor suas funções Lambda através de uma API REST, o AWS API Gateway pode ser usado para criar as rotas e endpoints necessários.

- **Tecnologia:** API Gateway cria e gerencia APIs RESTful de maneira escalável e segura.

- **Linguagem:** Não há uma linguagem específica aqui, pois o Gateway apenas direciona as requisições para as funções Lambda.

9. Monitoramento e Logs

- **AWS CloudWatch:** Para monitorar a execução das suas máquinas de estado, funções Lambda, e outros recursos. Isso permite que você colete métricas e veja logs detalhados das execuções para depuração e otimização.

## Exemplo de Pilha Tecnológica para esse Projeto

1. **Backend:**

    - AWS Step Functions (para orquestração).
    - WS Lambda (para executar as tarefas).
    - Node.js ou Python (para as funções Lambda).
    - AWS Bedrock (para IA generativa e sugestões).
    - AWS DynamoDB (para armazenamento de dados, se necessário).

2. **Infraestrutura:**

    - AWS CloudFormation ou Terraform (para gerenciamento de infraestrutura).
    - AWS SAM (para deploy de funções Lambda).

3. **Frontend (se necessário):**

    - React.js (para criar uma interface web interativa).

4. **APIs:**

    - AWS API Gateway (para expor as funções Lambda como APIs).
    - HTTP + JSON para comunicação entre o frontend e o backend.

5. **Monitoramento:**

    - AWS CloudWatch (para monitoramento de execuções e logs).

## Estrutura Sugerida para o Projeto

/Assistente_Delivery_AWS/
│
├── /src/                          # Código-fonte do projeto
│   ├── /lambda_functions/          # Funções Lambda usadas no projeto
│   │   ├── suggest_food.js         # Função Lambda para sugerir comida
│   │   ├── suggest_drink.js        # Função Lambda para sugerir bebida
│   │   ├── suggest_location.js     # Função Lambda para sugerir localização
│   │   └── compile_menu.js         # Função Lambda para compilar o menu
│   ├── /infra/                     # Infraestrutura como código
│   │   └── step_function.json      # Definição da máquina de estado no Step Functions (JSON)
│   └── /tests/                     # Testes para as funções Lambda (caso sejam implementados)
│       ├── test_suggest_food.js    # Teste para a função de sugestão de comida
│       ├── test_suggest_drink.js   # Teste para a função de sugestão de bebida
│       └── test_compile_menu.js    # Teste para a função de compilação de menu
│
├── /doc/                           # Documentação do projeto
│   └── e-book_aws_assistente_delivery.pdf  # E-book com explicações detalhadas sobre o projeto
│
├── README.md                       # Arquivo principal com explicações, JSON comentado e objetivos
└── .gitignore                      # Arquivo para ignorar dependências e arquivos desnecessários no Git

### Nota Importante

Os arquivos `.js` mencionados na estrutura acima, localizados na pasta **/lambda_functions/** e **/tests/**, estão **vazios**. Eles foram incluídos apenas como sugestões para um projeto completo, onde as funções Lambda e testes poderiam ser implementados para sugerir comida, bebida, localização e compilar um menu. A intenção é que eles sirvam de ponto de partida para futuras implementações.

## Código JSON do Step Functions (Comentado)

    {
    "Comment": "A workflow to create a complete menu suggestion with food, drink, and location",  /** Descrição geral do fluxo */
    "StartAt": "GetFoodSuggestion",  /** Estado inicial: Sugestão de Comida */
    "States": {
        "GetFoodSuggestion": {  /** Estado para obter sugestão de comida */
        "Type": "Task",
        "Resource": "arn:aws:states:::lambda:invoke",  /** Invoca a função Lambda */
        "Parameters": {
            "FunctionName": "arn:aws:lambda:REGION:ACCOUNT_ID:function:suggest-food",  /** Função Lambda sugerindo comida */
            "Payload": {}  /** Sem parâmetros adicionais */
        },
        "ResultPath": "$.menu.food",  /** O resultado é armazenado em $.menu.food */
        "Next": "GetDrinkSuggestion"  /** Próximo estado: Sugestão de Bebida */
        },
        "GetDrinkSuggestion": {  /** Estado para obter sugestão de bebida */
        "Type": "Task",
        "Resource": "arn:aws:states:::lambda:invoke",  /** Invoca a função Lambda */
        "Parameters": {
            "FunctionName": "arn:aws:lambda:REGION:ACCOUNT_ID:function:suggest-drink",  /** Função Lambda sugerindo bebida */
            "Payload": {}  /** Sem parâmetros adicionais */
        },
        "ResultPath": "$.menu.drink",  /** O resultado é armazenado em $.menu.drink */
        "Next": "GetLocationSuggestion"  /** Próximo estado: Sugestão de Localização */
        },
        "GetLocationSuggestion": {  /** Estado para obter sugestão de localização */
        "Type": "Task",
        "Resource": "arn:aws:states:::lambda:invoke",  /** Invoca a função Lambda */
        "Parameters": {
            "FunctionName": "arn:aws:lambda:REGION:ACCOUNT_ID:function:suggest-location",  /** Função Lambda sugerindo localização */
            "Payload": {}  /** Sem parâmetros adicionais */
        },
        "ResultPath": "$.menu.location",  /** O resultado é armazenado em $.menu.location */
        "Next": "CompileMenu"  /** Próximo estado: Compilação do Menu */
        },
        "CompileMenu": {  /** Estado para compilar o menu completo */
        "Type": "Task",
        "Resource": "arn:aws:states:::lambda:invoke",  /** Invoca a função Lambda */
        "Parameters": {
            "FunctionName": "arn:aws:lambda:REGION:ACCOUNT_ID:function:compile-menu",  /** Função Lambda que compila o menu */
            "Payload": {
            "menu.$": "$.menu"  /** Envia o menu gerado anteriormente como parâmetro */
            }
        },
        "ResultPath": "$.finalMenu",  /** O resultado final é armazenado em $.finalMenu */
        "End": true  /** Fim do fluxo de trabalho */
        }
    }
    }

## Como Executar o Projeto

### Pré-requisitos

- Uma conta na AWS.
- AWS CLI configurado no seu ambiente local.
- Serviços configurados no AWS Step Functions, Lambda, e Bedrock.

### Passos para Configuração

1. Clone este repositório:

    git clone <URL_DO_REPOSITORIO>

2. Implemente as funções Lambda necessárias no diretório /src/lambda_functions/ e faça o deploy delas na AWS Lambda.

3. Configure o arquivo step_function.json no Step Functions da AWS, atualizando o REGION e o ACCOUNT_ID com os valores apropriados da sua conta.

4. Teste o fluxo executando a máquina de estado diretamente pelo AWS Console ou AWS CLI.

### Licença

Este projeto é licenciado sob a MIT License.
