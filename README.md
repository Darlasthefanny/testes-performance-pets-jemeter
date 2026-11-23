 
 Testes de Performance com Apache JMeter — API Pets

📌 Sobre o projeto

Este projeto foi desenvolvido como parte do desafio prático de Testes de Performance com Apache JMeter.

O objetivo é avaliar o comportamento de uma API REST de cadastro de pets utilizando dois modelos de carga:

* Modelo fechado (Closed Model): simula uma quantidade definida de usuários virtuais executando requisições.
* Modelo aberto (Open Model): simula a chegada de requisições em uma taxa programada ao longo do tempo.

Os testes contemplam autenticação e operações de cadastro e consulta de pets.

🎯 Objetivos

* Implementar testes de performance utilizando Apache JMeter.
* Configurar um Thread Group com modelo de carga fechado.
* Configurar um Thread Group com modelo de carga aberto.
* Realizar autenticação antes das operações protegidas.
* Validar os endpoints POST /pets e GET /pets.
* Analisar os resultados obtidos durante as execuções.

🛠️ Tecnologias e ferramentas

* Apache JMeter 5.6.3
* API REST Cadastro de Pets
* Node.js
* HTTP
* JSON
* Git e GitHub

🧪 Cenários de teste

Os dois Thread Groups executam o seguinte fluxo:

1. Login — POST /login
    * Realiza a autenticação do usuário.
    * Extrai o token JWT da resposta utilizando JSON Extractor.
2. Cadastrar Pet — POST /pets
    * Envia uma requisição autenticada para cadastrar um pet.
    * Utiliza um nome dinâmico para evitar conflitos entre cadastros.
3. Consultar Pets — GET /pets
    * Realiza uma consulta autenticada dos pets cadastrados.

O token JWT é enviado no cabeçalho Authorization das requisições protegidas.

⚙️ Configuração da carga

1. Modelo fechado — TG_Modelo_Fechado

Configuração utilizada:

Parâmetro	Valor
Usuários virtuais	100
Ramp-up	100 segundos
Loop Count	5

Esse modelo permite avaliar o comportamento da API com uma quantidade definida de usuários simultâneos.

2. Modelo aberto — TG_Modelo_Aberto

Foi utilizado o componente Open Model Thread Group, com a seguinte programação:

rate(5/min) random_arrivals(2 min) pause(0 min)

Essa configuração programa a chegada de usuários de acordo com uma taxa de 5 por minuto, durante uma janela de 2 minutos.

📊 Resultados

Os resultados das execuções foram exportados em arquivos CSV e estão disponíveis neste repositório:

* resultado-modelo-fechado.csv
* resultado-modelo-aberto.csv

Os relatórios permitem consultar métricas como:

* Quantidade de requisições executadas.
* Tempo médio de resposta.
* Tempo mínimo e máximo de resposta.
* Percentual de erros.
* Throughput (vazão de requisições).

📁 Estrutura do projeto

testes-performance-pets-jemeter/
│
├── testes-performance-pets.jmx
├── resultado-modelo-fechado.csv
├── resultado-modelo-aberto.csv
└── README.md

▶️ Como executar o projeto

1. Instale o Apache JMeter 5.6.3 ou versão compatível.
2. Inicie a API Cadastro de Pets e confirme que está disponível em http://localhost:3000.
3. Faça o download do arquivo testes-performance-pets.jmx.
4. Abra o arquivo no Apache JMeter.
5. Confira as configurações dos dois Thread Groups.
6. Execute os testes e consulte os resultados nos listeners Summary Report, Aggregate Report e View Results Tree.

Importante: a API precisa estar em execução durante os testes. As credenciais e os dados utilizados devem corresponder aos cadastrados na API.

📌 Considerações finais

O projeto possibilitou a aplicação prática de conceitos de testes de performance, autenticação JWT, simulação de usuários virtuais e análise de métricas utilizando Apache JMeter.

Foram implementados dois modelos de carga, permitindo observar o comportamento da API em diferentes estratégias de geração de requisições.

⸻

Ferramenta principal: Apache JMeter 5.6.3
Tipo de projeto: Testes de Performance em API REST
Repositório: GitHub — testes-performance-pets-jemeter
