# SIR\_ChatGPT
Development of a Simple Informational Retrieval System obtaining guidance with ChatGPT. Tested on CISI collection with BM25 algorithm.

### Github do Projeto: 
<https://github.com/marcusborela/Sir-ChatGPT.git> 
### Autor: 
Marcus Vinícius Borela de Castro (<marcusborela@yahoo.com.br>) 

## Índice

- [SIR\_ChatGPT](#sir_chatgpt)
    - [Github do Projeto:](#github-do-projeto)
    - [Autor:](#autor)
  - [Índice](#índice)
  - [Contexto](#contexto)
    - [Project Overview:](#project-overview)
    - [Project Outcomes:](#project-outcomes)
    - [Project Requirements:](#project-requirements)
    - [Project Deliverables:](#project-deliverables)
    - [Evaluation:](#evaluation)
  - [Estudo prévio sobre ChatGpt](#estudo-prévio-sobre-chatgpt)
    - [Sites com reflexões e dicas sobre o chatbot](#sites-com-reflexões-e-dicas-sobre-o-chatbot)
    - [Extensões do Google Chrome](#extensões-do-google-chrome)
  - [Conversas preliminares](#conversas-preliminares)
  - [Desenvolvimento do projeto](#desenvolvimento-do-projeto)
    - [Chats durante o desenvolvimento da solução](#chats-durante-o-desenvolvimento-da-solução)
    - [Relatório Fase 1 - Compreensão do Negócio](#relatório-fase-1---compreensão-do-negócio)
      - [1.1 CISI Collection](#11-cisi-collection)
      - [1.2 Information Retrieval System (IR system)](#12-information-retrieval-system-ir-system)
      - [1.3 BM25](#13-bm25)
      - [1.4 Métricas de Relevância para Avaliação de IR](#14-métricas-de-relevância-para-avaliação-de-ir)
    - [Precisão (Precision)](#precisão-precision)
        - [Revocação (Recall)](#revocação-recall)
        - [F1-Score](#f1-score)
        - [Mean Average Precision (MAP)](#mean-average-precision-map)
        - [1.4.5 R-Precision](#145-r-precision)
        - [1.4.6 NCG (Normalized Cumulative Gain)](#146-ncg-normalized-cumulative-gain)
    - [Relatório Fase 2 - Implementação](#relatório-fase-2---implementação)
      - [Coleta de dados da CISI Collection](#coleta-de-dados-da-cisi-collection)
      - [Pré-processamento dos textos de documentos e consultas](#pré-processamento-dos-textos-de-documentos-e-consultas)
      - [Implementação de dois mecanismos de busca com BM25](#implementação-de-dois-mecanismos-de-busca-com-bm25)
        - [BM25](#bm25)
        - [BM25\_Penaliza\_Tamanho\_Docto](#bm25_penaliza_tamanho_docto)
    - [Relatório Fase 3 - Avaliação de mecanismos de busca](#relatório-fase-3---avaliação-de-mecanismos-de-busca)
  - [Reflexões sobre a interação com o ChatGPT](#reflexões-sobre-a-interação-com-o-chatgpt)
    - [Limitações](#limitações)
      - [Parece haver um limite no tamanho do texto gerado pelo WebChatGPT.](#parece-haver-um-limite-no-tamanho-do-texto-gerado-pelo-webchatgpt)
      - [Parece haver um limite no tamanho do prompt gerado pelo WebChatGPT.](#parece-haver-um-limite-no-tamanho-do-prompt-gerado-pelo-webchatgpt)
    - [Não sabe sempre](#não-sabe-sempre)
    - [Às vezes complica e parece inventar coisas](#às-vezes-complica-e-parece-inventar-coisas)
    - [Formato do prompt é importante](#formato-do-prompt-é-importante)
    - [Funcionalidades faltando](#funcionalidades-faltando)
      - [Falta um CRUD básico de chats no WebChatGPT](#falta-um-crud-básico-de-chats-no-webchatgpt)
      - [Poderia ler sites da web](#poderia-ler-sites-da-web)
    - [Inventa coisas](#inventa-coisas)
    - [Às vezes é pró-ativo](#às-vezes-é-pró-ativo)
    - [Erros no sistema](#erros-no-sistema)
      - [“An error occurred. If this issue persists please contact us through our help center at help.openai.com. “](#an-error-occurred-if-this-issue-persists-please-contact-us-through-our-help-center-at-helpopenaicom-)
      - ["Too many requests in 1 hour. Try again later."](#too-many-requests-in-1-hour-try-again-later)
      - [“ChatGPT is at capacity right now.  Get notified when we're back”](#chatgpt-is-at-capacity-right-now--get-notified-when-were-back)
      - [“An error occurred. Either the engine you requested does not exist or there was another issue processing your request. If this issue persists please contact us through our help center at help.openai.com.”](#an-error-occurred-either-the-engine-you-requested-does-not-exist-or-there-was-another-issue-processing-your-request-if-this-issue-persists-please-contact-us-through-our-help-center-at-helpopenaicom)
    - [Falta uma maior clareza nas mensagens de erro](#falta-uma-maior-clareza-nas-mensagens-de-erro)
    - [Há muito truncamento de resposta](#há-muito-truncamento-de-resposta)
    - [Tentei me cadastrar como usuário ChatGPT Plus, mas não está aberto para usuários fora dos EUA](#tentei-me-cadastrar-como-usuário-chatgpt-plus-mas-não-está-aberto-para-usuários-fora-dos-eua)
    - [Melhor dividir em passos/perguntas menores](#melhor-dividir-em-passosperguntas-menores)
    - [Exige compreensão dos conceitos](#exige-compreensão-dos-conceitos)
    - [Às vezes é necessário apertar o botão “stop generating”](#às-vezes-é-necessário-apertar-o-botão-stop-generating)
    - [Conclusão](#conclusão)
  - [Referências interessantes](#referências-interessantes)

## Contexto 
(deixei próximas seções em inglês para ser fiel à documentação recebida da Unicamp).

Unicamp Training Selection. Exercise for special student selection - Course "Deep Learning applied to searches", FEEC-Unicamp, first half of 2023.

Objective

To develop a small Information Retrieval project with the freedom to use chatGPT to help you in all phases of the project:

- to learn about IR,
- to code it in Python, and
- to write the report.

### Project Overview:
The aim of this project is to introduce students to the basics of Information Retrieval (IR) and the BM25 ranking algorithm. 

The sollution to this project will help us to select the students to attend the course on deep learning applied to search. The students will build a simple IR system that retrieves relevant documents from a pre-defined corpus based on the user's query. The students will also use the chatGPT to assist in all phases of the project. 

The coding will be done using Google Colab notebooks and the deliverables will be placed in github account.
### Project Outcomes:
Upon completion of the project, students will have gained the following skills:

- Understanding of the BM25 ranking algorithm
- Familiarity with Information Retrieval systems
- Use of GitHub to store the notebooks and documentation
- Experience with chatGPT for help in find solutions and coding
- Exposure to Google Colab notebooks for code execution and presentation.
### Project Requirements:
- Google Colab Notebook
- GitHub account
- chatGPT for help on all aspects of the project
- CISI collection: http://ir.dcs.gla.ac.uk/resources/test\_collections/cisi/
- Familiarity with Python programming
### Project Deliverables:
A github repository with:

- - link shared with the instructors to evaluate the project contents
- - all Google Colab notebooks and associated functions and libraries if any, with the code for the IR system
- - A brief report describing the implementation details, results, how to test the IR system and how chatGPT helped you with the project.
### Evaluation:
The project will be evaluated based on the following criteria:

- Completion of the project deliverables (partial is OK to submit)
- Implementation accuracy
- Quality of the report
- Code readability and commenting
- How chatGPT was used
## Estudo prévio sobre ChatGpt 
Antes de iniciar o projeto assistido pelo ChatGPT, precisava me atualizar sobre suas capacidades e desejava descobrir algumas ferramentas de apoio. Por isso criei esta seção.

Perguntei ao ChatGPT “o que é ChatGPT”, e ele respondeu:

“ChatGPT é um modelo de linguagem de inteligência artificial criado pela OpenAI. Ele é projetado para conversar com usuários em linguagem natural, respondendo a perguntas, fornecendo informações e até mesmo fazendo pequenas conversas. O ChatGPT foi treinado em uma grande quantidade de dados de linguagem natural para aprender a entender a linguagem humana e gerar respostas relevantes e coerentes. Ele é capaz de conversar sobre uma ampla variedade de tópicos e pode ser usado em diversas aplicações, desde assistentes de bate-papo em sites até chatbots em redes sociais.”
### Sites com reflexões e dicas sobre o chatbot
1. [Chatbots interessantes](https://olhardigital.com.br/2023/02/14/internet-e-redes-sociais/10-chatbots-similares-ao-chatgpt-para-voce-testar/)
1. [Google emite “alerta vermelho” após ChatGPT](https://www.showmetech.com.br/chatgpt-faz-google-emitir-alerta-vermelho/)
1. [Coding Won’t Exist In 5 Years. This Is Why](https://javascript.plainenglish.io/coding-wont-exist-in-5-years-this-is-why-6da748ba676c)
1. [Inteligência artificial do Google tem consciência própria, afirma engenheiro](https://www.showmetech.com.br/inteligencia-artificial-do-google-tem-consciencia/)
1. [Engenheiro diz que IA do Google contratou seu próprio advogado](https://www.showmetech.com.br/ia-do-google-contratou-seu-proprio-advogado/)
1. [ChatGPT’s History Vanishes: How to Recover Your Lost Data](https://medium.com/gptcommands/chatgpts-history-vanishes-how-to-recover-your-lost-data-d08f42fc87ee)
1. [ChatGPT tutorial: How to improve your work with ChatGPT](https://lablab.ai/t/chatgpt-how-to-improve-your-work-with-chatgpt)
1. [Advanced ChatGPT Prompt Tutorial (10X Your Productivity With AI)](https://www.youtube.com/watch?v=HGDxu3kPErs)
1. [10 Awesome ChatGPT Extensions To Improve Your Life](https://beingpax.medium.com/10-awesome-chatgpt-extensions-to-improve-your-life-590a530ddde6)
1. [ChatGPT tutorial: How to easily improve your coding skills with ChatGPT](https://lablab.ai/t/chatgpt-tutorial-how-to-easily-improve-your-coding-skills-with-chatgpt)
1. [ChatGPT tutorial: How to improve your work with ChatGPT](https://lablab.ai/t/chatgpt-how-to-improve-your-work-with-chatgpt)
1. [Get The Best ChatGPT Experience With These 10 Chrome Extensions](https://geekflare.com/best-chatgpt-chrome-extensions/)

### Extensões do Google Chrome 
(em ordem de importância, critério subjetivo do autor)
1. [WebChatGPT: ChatGPT com acesso à internet](https://chrome.google.com/webstore/detail/webchatgpt-chatgpt-with-i/lpfemeioodjbpieminkklglpmhlngfcn): permite busca informações atualizadas. Como o gpt-3 foi treinado em 2021, ele não traz respostas atualizadas (exemplo: quem é o presidente do Brasil?). Essa extensão permite que o chatgpt faça uma busca atualizada (configurável: período, número de resultados, etc) o que o torna ainda mais utilizável.
1. [YouTube Summary with ChatGPT](https://chrome.google.com/webstore/detail/youtube-summary-with-chat/nmmicjeknamkfloonkhhcjmomieiodli): gera sumário do vídeo no youtube
magem (jpg).
1. [ChatGPT for Google](https://chrome.google.com/webstore/detail/chatgpt-for-google/jgjaeacdkonaoafenlfkkkmbaopkbilf): responde em pesquisas no google. Configurável, permite, por exemplo, apagar de forma automática os chats no openai.1. [FancyGPT](https://chrome.google.com/webstore/detail/fancygpt/meonalmakdjaojaoipfhahcfccoecegk?hl=pt-BR): salva como pdf, txt ou i
1. [AI Content Detector - Copyleaks](https://chrome.google.com/webstore/detail/ai-content-detector-copyl/gplcmncpklkdjiccbknjjkoidpgkcakd?hl=pt-BR): avalia se página (ou texto) foi gerada por robô.
1. [ChatGPT Prompt Genius](https://chrome.google.com/webstore/detail/chatgpt-prompt-genius/jjdnakkfjnnbbckhifcfchagnpofjffo): salva a história de chats localmente (podem ser exportados, tornando públicos). Bom para não depender apenas da OpenAi que está sendo sobrecarregada. Permite consulta de outros chats público. E exportar conversa para pdf/html/png/markdown. Código aberto no [GitHub](https://github.com/benf2004/ChatGPT-Prompt-Genius). 
1. [Copy for Chat GPT](https://chrome.google.com/webstore/detail/copy-for-chat-gpt/mloblghgjiagjdffmgobhbgmplhongpm): permite copiar a resposta e passar por um detector de plágio (Atalho: CMD + k). Código aberto.
1. [Save ChatGPT](https://chrome.google.com/webstore/detail/save-chatgpt/iccmddoieihalmghkeocgmlpilhgnnfn): exporta conversa em texto. Embora seja mais rápida, removi, pois optei por usar a FancyGPT, que além de permitir salvar como texto, dá opões de pdf e imagem (jpeg). 
1. [ChatGPT Assistant - Use AI Everywhere](https://chrome.google.com/webstore/detail/chatgpt-assistant-use-ai/kldepdcdedfibmjnggmolhffdddbphjg): permite dar um “right click” em um texto e enviar ao chatgpt (atalho Ctrl + Shift + K). Se mostra interessante. Mas, removi pois optei por usar o Prompt Genius ao invés desse.
1. [Glarity - Summary for Google with ChatGPT](https://chrome.google.com/webstore/detail/glarity-summary-for-googl/cmnlolelipjlhfkhpohphpedmkfbobjc?hl=pt-BR): sumariza páginas de resposta do google. Mas concorre com a extensão ChatGPT for Google (não permite a resposta desta). Por isso a desativei. Também faz um sumário do vídeo no youtube, o que já é tratado na extensão [YouTube Summary with ChatGPT](https://chrome.google.com/webstore/detail/youtube-summary-with-chat/nmmicjeknamkfloonkhhcjmomieiodli).
## Conversas preliminares

1. [Dica nutricional para crianças diabéticas](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Conversas%20preliminares%20com%20WebChatGPT/Dica%20nutricional%20para%20crian%C3%A7as%20diab%C3%A9ticas.pdf)
1. [Esclarecendo sobre questão de saude hemicupula elevada](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Conversas%20preliminares%20com%20WebChatGPT/Esclarecendo%20sobre%20quest%C3%A3o%20de%20saude%20hemicupula%20elevada.pdf)
1. [Incentivo aos filhos para usarem ChatGpt](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Conversas%20preliminares%20com%20WebChatGPT/Incentivo%20aos%20filhos%20para%20usarem%20ChatGpt.pdf)

## Desenvolvimento do projeto

### Chats durante o desenvolvimento da solução
[Contextualização do projeto, definção de fases e execução da fase compreensão do negócio, incluindo a criação do Relatório Fase 1 (ver abaixo)](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/SirChatGPT%20desenvolvimento.md)


[Dúvidas avulsas (github, markdown, nomenclaturas, codificação fora do contexto de desenvolvimento, etc)](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/D%C3%BAvidas%20avulsas.md)

A implementação e a avaliação da solução foram tratados em um único chat. 

[Na fase de implementação, com todas as suas etapas, houve uma programação em par (pair programming) em um único chat](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/SirChatGPT%20desenvolvimento.md)

Para legibilidade e clareza, dividimos esse chat em 3 chats complementares que se seguem:

[Programação em Par (pair programming) para a codificação das etapas de coleta de dados e de pré-processamento](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/Coleta%20de%20dados%20e%20pr%C3%A9-processamento.md)


[Programação em Par (pair programming) para a codificação da etapa de implementação do mecanismo de busca](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/Implementa%C3%A7%C3%A3o%20mecanismos%20de%20busca.md)

[Programação em Par (pair programming) para a codificação da etapa de avaliação do mecanismo de busca](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/Avalia%C3%A7%C3%A3o%20de%20mecanismo%20de%20busca.md)


### Relatório Fase 1 - Compreensão do Negócio
[(O relatório abaixo foi criado integralmente pelo ChatGPT ao final do diálogo que inclui a contextualização até a conclusão da fase de compreensão dos conceitos envolvidos no negócio. Só foi necessário um ajuste nas fórmulas das métricas r-precision e ncg.)](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/Contextualizacao%20e%20compreensao%20do%20negocio.md)
#### 1.1 CISI Collection
A CISI Collection é um conjunto de dados coletados pelo Centro de Invenções e Informação Científica (CISI) e é composto por cerca de 1460 documentos e 112 consultas associadas. O objetivo dessa coleção é ser usada para construir modelos de recuperação de informação, em que uma determinada consulta retornará uma lista de IDs de documentos relevantes à consulta.
#### 1.2 Information Retrieval System (IR system)
Um sistema de recuperação de informação (IR system) é um sistema que permite aos usuários encontrar informações relevantes para suas necessidades de informação. Os sistemas de recuperação de informação geralmente trabalham com grandes quantidades de dados não estruturados e permitem que os usuários recuperem informações usando palavras-chave, frases ou consultas complexas.

Os principais módulos de um sistema de recuperação de informação são:

- <strong>Coleta de dados</strong>: coleta de dados a partir de fontes como a web, bancos de dados, arquivos de texto, etc.
- <strong>Pré-processamento</strong>: processamento dos dados coletados para melhorar a qualidade e a eficácia da recuperação da informação. Inclui a limpeza dos dados, remoção de stop words, stemming, entre outros.
- <strong>Indexação</strong>: criação de um índice que mapeia as palavras encontradas nos documentos e consultas a seus respectivos documentos.
- <strong>Recuperação</strong>: comparação das consultas com o índice criado na etapa anterior e retorno dos documentos relevantes para a consulta.
- <strong>Avaliação</strong>: avaliação da eficácia do sistema de recuperação de informação. Isso inclui o cálculo de métricas de avaliação de recuperação, como precisão, revocação, F-measure, MAP, entre outras.

#### 1.3 BM25
O BM25 é um algoritmo de ranqueamento de documentos amplamente utilizado em sistemas de recuperação de informação. Foi proposto por Robertson e colaboradores em 1995. A fórmula do BM25 é dada por:

```
score(D,Q) = ∑(i∈Q) IDF(i) * ((k + 1) * tf(i,D)) / (k * (1 - b + b * (|D| / avgdl)) + tf(i,D))

```

onde:

- `D` é um documento;
- `Q` é uma consulta;
- `tf(i,D)` é o número de vezes que o termo `i` aparece no documento `D`;
- `|D|` é o comprimento do documento `D` em termos de número de palavras;
- `avgdl` é o comprimento médio de todos os documentos na coleção;
- `k` e `b` são constantes de ajuste do BM25;
- `IDF(i)` é o inverso da frequência do documento para o termo `i` calculado como `log((N - n(i) + 0.5) / (n(i) + 0.5))`, onde `N` é o número de documentos na coleção e `n(i)` é o número de documentos que contêm o termo `i`.

#### 1.4 Métricas de Relevância para Avaliação de IR
As principais métricas

As métricas de relevância são usadas para avaliar a eficácia de um sistema de recuperação de informações, determinando a relevância dos documentos recuperados para uma consulta. Algumas das principais métricas de relevância incluem:
### Precisão (Precision)
A precisão é a proporção de documentos recuperados que são relevantes para uma determinada consulta. É calculada pela fórmula:

```
Precision = |Documentos relevantes recuperados| / |Documentos recuperados|

```

Onde:

- `|Documentos relevantes recuperados|`: número de documentos relevantes recuperados pelo sistema para a consulta.
- `|Documentos recuperados|`: número total de documentos recuperados pelo sistema para a consulta.

##### Revocação (Recall)
A revocação é a proporção de documentos relevantes que foram recuperados pelo sistema em relação ao número total de documentos relevantes. É calculada pela fórmula:

```
Recall = |Documentos relevantes recuperados| / |Documentos relevantes|

```

Onde:

- `|Documentos relevantes recuperados|`: número de documentos relevantes recuperados pelo sistema para a consulta.
- `|Documentos relevantes|`: número total de documentos relevantes para a consulta.

##### F1-Score
O F1-score é uma medida que combina precisão e revocação em uma única métrica. É calculado pela fórmula:

```
F1 = 2 * (precision * recall) / (precision + recall)

```
##### Mean Average Precision (MAP)
O MAP é uma medida que leva em conta a ordem dos documentos recuperados pelo sistema. Ele considera não apenas a precisão e a revocação, mas também o rank dos documentos relevantes retornados pelo sistema. O MAP é calculado pela fórmula:

```
MAP = (1/|Q|) * ∑_(i=1)^|Q| (1/rel_i) * ∑_(j=1)^|k| (P_j * rel_j)

```

Onde:

- `|Q|`: número de consultas no conjunto de consultas.
- `rel_i`: número total de documentos relevantes para a consulta `i`.
- `k`: número máximo de documentos recuperados pelo sistema para a consulta `i`.
- `P_j`: precisão na posição `j` dos documentos recuperados para a consulta `i`.
- `rel_j`: indicador binário que indica se o documento na posição `j` é relevante ou não para a consulta `i`.


O MAP é uma medida útil para avaliar sistemas de recuperação de informações que retornam uma lista ordenada de documentos relevantes, como motores de busca.

##### 1.4.5 R-Precision
A métrica R-Precision é definida como a precisão dos primeiros R documentos recuperados para uma determinada consulta, onde R é o número de documentos relevantes para essa consulta. É uma métrica utilizada principalmente quando o número de documentos relevantes é conhecido. A fórmula para calcular a R-Precision é dada por:

$$R-Precision = \frac{\text{Número de documentos relevantes nos primeiros R resultados}}{min(R, topk)}$$

##### 1.4.6 NCG (Normalized Cumulative Gain)
A métrica NCG (Normalized Cumulative Gain) é utilizada para medir a eficácia de um sistema de recuperação de informação, levando em consideração a posição de cada item na lista de resultados. A métrica assume que as avaliações de relevância são binárias, ou seja, um item é relevante ou não relevante. A NCG normaliza a medida de ganho acumulado (CG) pelo ideal máximo de ganho acumulado (ICG), a fim de levar em conta o número de itens relevantes.

A fórmula da NCG é dada por:

$$NCG@k = \frac{CG@k}{ICG@k}$$

Onde:

- $CG@k$ é o ganho acumulado na posição $k$.
- $ICG@k$ é o ganho acumulado ideal na posição $k$.


O ganho acumulado ideal (ICG) na posição $k$ é calculado da seguinte forma:

$$ICG@k = \sum_{i=1}^k relideal_i$$

Onde:

- $relideal_i$ é o nível de relevância do documento na posição $i$ (0 ou 1) considerando que todos os relevantes fossem retornados no início do resultado em ordem decrescente de relevância.



O ganho acumulado (CG) na posição $k$ é dado por:

$$CG@k = \sum_{i=1}^k rel_i$$

Onde:

- $rel_i$ é o nível de relevância do documento na posição $i$ (0 ou 1) dos documentos realmente retornados na busca.


Assim, a métrica NCG varia de 0 a 1, onde valores mais próximos de 1 indicam um sistema mais eficaz na recuperação de informações relevantes.


Obs.: o relatório que se segue foi criado parcialmente (complementei e corrigi informações) pelo ChatGPT ao final dos diálogos acima indicados que abarcam cada fase.
### Relatório Fase 2 - Implementação 


Foi desenvolvida uma implementação em Python e o código é executado em ambiente google colab. Foram implementadas as seguintes etapas

#### Coleta de dados da CISI Collection

A coleção de documentos CISI é uma coleção de documentos acadêmicos que foi compilada por C. J. van Rijsbergen da Universidade de Glasgow. A coleção consiste em cerca de 15.000 resumos de artigos da área de Ciência da Informação, extraídos de revistas publicadas entre 1958 e 1972. Trata-se de um conjunto de documentos de teste amplamente utilizado em pesquisas de recuperação de informações. É composto por um total de 1460 documentos e 112 consultas. E traz uma associação entre consultas e seus documentos relevantes. 


A implementação desenvolvida permite a coleta dos dados da coleção CISI diretamente do site oficial da Universidade de Glasgow, onde os dados estão disponíveis para download.


Para a coleta de dados da CISI Collection, foram utilizados os seguintes passos:

1. Baixar a coleção de documentos da CISI Collection de um repositório público;
2. Extrair o conteúdo dos arquivos ZIP baixados para uma pasta local;
3. Ler cada documento individualmente e armazenar seu conteúdo em uma estrutura de dados, como um dicionário, onde cada chave é o identificador do documento e o valor é o conteúdo do documento.
#### Pré-processamento dos textos de documentos e consultas

A implementação desenvolvida realiza as seguintes etapas de pré-processamento nos textos dos documentos e consultas: 

Conversão dos caracteres para minúsculas: Os caracteres são convertidos para minúsculas, para evitar ambiguidades devido à diferença de capitalização entre as palavras.

Remoção de caracteres especiais: Caracteres especiais, como pontos, vírgulas, parênteses, colchetes e chaves, são removidos para evitar a interferência desses caracteres na análise do texto.

Remoção de stopwords: Stopwords, que são palavras comuns que não contribuem significativamente para o significado do texto, são removidas para evitar a interferência dessas palavras na análise do texto.

Lematização: A lematização é um processo de normalização do texto, que consiste em reduzir as palavras às suas formas básicas (lemas), removendo as variações de tempo, número, gênero e modo. Esse processo ajuda a reduzir a dimensionalidade do espaço de características e a melhorar a precisão da análise do texto.

A implementação permite a configuração da combinação de técnicas de pré-processamento desejada, permitindo que o usuário selecione quais técnicas serão aplicadas.

A fução permite a flexibilidade de configurar a combinação de técnicas desejada. Foram elaborados testes de algumas funções utilizando a chamada do comando assert.

#### Implementação de dois mecanismos de busca com BM25

Foram criadas duas classes que implementam o modelo de ranqueamento BM25 para buscas em documentos. A primeira classe, denominada BM25, é implementada do zero e faz uso da biblioteca scikit-learn para calcular a matriz TF-IDF dos documentos. A segunda classe, denominada BM25_Penaliza_Tamanho_Docto, faz uso da biblioteca rank-bm25 para implementar o modelo BM25 e também considera o tamanho dos documentos durante o ranqueamento.

##### BM25

A classe BM25 implementa o modelo de ranqueamento BM25 para buscas em documentos. O modelo BM25 é uma função que mede a similaridade entre um documento e uma consulta. A implementação do modelo BM25 na classe BM25 leva em conta o número de ocorrências de um termo no documento, o número total de documentos na coleção, a frequência do termo na coleção e o comprimento do documento. A implementação do modelo BM25 é feita através do cálculo da pontuação BM25 de cada documento da coleção em relação à consulta, conforme Paiva (2020).

A classe BM25 recebe como parâmetro uma lista de documentos pré-processados, juntamente com os parâmetros k1 e b, que são utilizados na equação acima para ajustar a frequência dos termos e o comprimento dos documentos. Para calcular a matriz TF-IDF dos documentos, a classe faz uso da biblioteca scikit-learn.

A classe BM25 possui as seguintes funcionalidades:

. _score(query_tf_idf, index): método que calcula a pontuação BM25 para um documento específico em relação a uma consulta. O método recebe como parâmetros o vetor TF-IDF da consulta e o índice do documento;

. search(query, k=5): método que busca os k documentos mais relevantes para a consulta query. O método recebe como parâmetros a consulta e o número de documentos a serem retornados.

##### BM25_Penaliza_Tamanho_Docto

A classe BM25_Penaliza_Tamanho_Docto também implementa o modelo de ranqueamento BM25 para buscas em documentos, mas leva em conta o tamanho dos documentos durante o ranqueamento. A implementação do modelo BM25 considerando o tamanho dos documentos é feita através da biblioteca rank-bm25, que já possui uma implementação do modelo BM25 com essa consideração.

A classe BM25_Penaliza_Tamanho_Docto recebe como parâmetro uma lista de documentos pré-processados. 
Trata-se de uma variação do algoritmo BM25 que leva em consideração o tamanho do documento ao calcular a relevância de um termo de busca para um documento. A fórmula básica do BM25 considera apenas o número de ocorrências de um termo no documento e no corpus. No entanto, documentos mais longos podem ter uma contagem de ocorrências mais alta simplesmente porque têm mais palavras. Isso pode levar a uma classificação incorreta dos resultados da pesquisa.

Para corrigir essa distorção, o BM25_Penaliza_Tamanho_Docto ajusta a contagem de ocorrências de um termo no documento com base no tamanho do documento em relação a um comprimento médio esperado. Isso é feito com a introdução de um fator de normalização que penaliza documentos mais longos e recompensa documentos mais curtos. O fator de normalização é calculado como (k1 * (1-b + b * (len_d / avg_len))) + 1, onde k1 e b são parâmetros ajustáveis, len_d é o comprimento do documento em questão e avg_len é o comprimento médio dos documentos no corpus.

A classe possui a seguinte funcionalidade:

. search(query, k=5): método que busca os k documentos mais relevantes para a consulta query. O método recebe como parâmetros a consulta e o número de documentos a serem retornados.


### Relatório Fase 3 - Avaliação de mecanismos de busca


A tabela abaixo apresenta a média das métricas obtidas pelos mecanismos de busca avaliados:
<table><thead><tr><th>Métrica</th><th>BM25</th><th>BM25 com penalização por tamanho do documento</th></tr></thead><tbody><tr><td>Precisão</td><td>0.2868</td><td>0.0211</td></tr><tr><td>R-Precisão</td><td>0.3016</td><td>0.0211</td></tr><tr><td>NCG</td><td>0.3016</td><td>0.0211</td></tr></tbody></table>

Com base nos resultados obtidos, podemos concluir que para a coleção CISI o mecanismo_bm25 teve um desempenho significativamente melhor do que o mecanismo_bm25_penaliza_tamanho em relação às métricas apuradas de precisão, r-precisão e ncg (Normalized Cumulative Gain).


Observações complementares:
. No caso da coleção CISI, como não há valor de relevância diferente de um, a aplicabilidade da métrica ncg fica comprometida. Algo a investigar é se nesses casos o valor de ncg se equivale ao de r-precision, conforme foi apurado nos cálculos. 

. O mesmo resultado nas 3 métricas para o mecanismo BM25 com penalização por tamanho do documento é estranho. Os códigos das métricas e os cálculos foram testados para diferentes consultas e para todos os mecanismos. E não foi encontrada causa desse comportamento. Não se  descarta a necessidade de uma nova revisão do código. Mas sugere-se começar por uma avaliação se foi correto o uso da library rank_bm25 com sua classe M25Okapi.


## Reflexões sobre a interação com o ChatGPT

As anotações abaixo precisam ser agrupadas e revisadas. Mas são alguns pontos importantes sobre a interação com o WebChatGPT durante todo o projeto.

### Limitações
#### Parece haver um limite no tamanho do texto gerado pelo WebChatGPT. 

 Quando solicitei o relatório de compreensão do negócio, por 2 vezes ele interrompeu: a primeira sem a seção 1.4, a segunda só com a primeira frase dessa seção. Isso também aconteceu na seção 1.4.5 quando aumentei o número de métricas.

#### Parece haver um limite no tamanho do prompt gerado pelo WebChatGPT. 

Quando fui passar o diálogo anterior como contexto, recebi mensagem: The message you submitted was too long, please reload the conversation and submit something shorter.


### Não sabe sempre
Às vezes erra nos exemplos (ver caso de r-precision). O denominador não poderia ser maior do que o número de documentos relevantes.

### Às vezes complica e parece inventar coisas
Às vezes passa a fórmula mais complexa: ver caso da fórmula passada inicialmente para NCG. Baseava-se em DCG. Como estava acompanhando com a leitura de um artigo, solicitei que reformulasse baseando-se apenas em ICG (ideal).

### Formato do prompt é importante
O formato do prompt é importante. Para que ele entenda o que é para fazer. Solicitei para ele gerar apenas um complemento de uma seção, mas ele gerou a seção inteira.

. Ele estava gerando fórmulas nem sempre em formato markdown  compreensíveis pelo github. A partir do comando “Importante: sempre escrever fórmulas em markdown compreensível pelo github”, as fórmulas vieram em formato certo.

Pedi: A função search ficou incompleta. Favor gerar apenas o código da função search.
. Muitas vezes gera tudo novamente. E diferente da versão anterior.

### Funcionalidades faltando
#### Falta um CRUD básico de chats no WebChatGPT
Poderia possuir opção, por exemplo, de editar com exclusão de perguntas e respostas e reaplicar o chat.


#### Poderia ler sites da web
Perguntei: Você consegue ler sites da web?

Resposta: Sim, como modelo de linguagem, eu posso ler e processar texto em sites da web, bem como em outros tipos de documentos. No entanto, como um assistente de linguagem, não tenho acesso direto à internet e não sou capaz de navegar na web. Meu papel é responder a perguntas e fornecer informações com base no meu conhecimento prévio, que foi adquirido a partir de um conjunto de dados limitado e treinamento supervisionado.

### Inventa coisas
Às vezes entra com um “papo” de que já está sabendo algo, no caso uma conversa anterior (presunçoso?).
. Olá Marcus, é um prazer conversar com você e ser seu consultor no projeto. Claro, pode me chamar de CG e podemos começar sim. Já estou ciente da conversa anterior e li a seção correspondente no Github. Estou à disposição para ajudar nas próximas fases do projeto. Vamos em frente!
. Estava ciente nada. Perguntei: “Se você sabe, gostaria de saber quais as métricas que compõem a seção 1.4 de métricas?”. E ele trouxe métricas diferentes. Daí recomecei o chat sem essas métricas incorretas.

### Às vezes é pró-ativo
Ele gerou uma Análise Exploratória de Dados da CISI Collection. Mas não era o que eu queria no momento. Precisei mudar o prompt.

### Erros no sistema
####  “An error occurred. If this issue persists please contact us through our help center at help.openai.com. “
(Eu não havia colocado pergunta, apenas apresentado a contextualização e as fases pensadas para o desenvolvimento do projeto. Mudei para encerrar com a mensagem: “A seguir te passarei o relatório da Fase 1.” e deu certo.

#### "Too many requests in 1 hour. Try again later."
#### “ChatGPT is at capacity right now.  Get notified when we're back”

#### “An error occurred. Either the engine you requested does not exist or there was another issue processing your request. If this issue persists please contact us through our help center at help.openai.com.”

### Falta uma maior clareza nas mensagens de erro
Quando a minha internet estava fora, deu a seguinte mensagem de erro:

“An error occurred. Either the engine you requested does not exist or there was another issue processing your request. If this issue persists please contact us through our help center at help.openai.com.”

### Há muito truncamento de resposta 
Ocorreu várias vezes na geração do código BM25 que é um pouco maior.

### Tentei me cadastrar como usuário ChatGPT Plus, mas não está aberto para usuários fora dos EUA
. ChatGPT Plus is available to customers in the United States, and we will begin the process of inviting people from our waitlist over the coming weeks. We plan to expand access and support to additional countries and regions soon.

. We love our free users and will continue to offer free access to ChatGPT. By offering this subscription pricing, we will be able to help support free access availability to as many people as possible.

.Pedi para entrar na waitlist.


### Melhor dividir em passos/perguntas menores
Para obter respostas mais corretas (na codificação, principalmente)
 

### Exige compreensão dos conceitos
Sofri no BM25 com os erros nos códigos gerados. Tive que compreender toda a lógica para ajustar o código.

### Às vezes é necessário apertar o botão “stop generating”
No final, aprendi a usar “stop generating” quando via que de início ele seguia por caminhos equivocados.

### Conclusão
Achei muito enriquecedora a experiência. Foi de grande ajuda.

Acredito  que serão criados treinamentos específicos para ensinar a codificar com o WebChatGPT, dando dicas sobre os formatos dos prompts e como conduzir uma conversa.

## Referências interessantes
PAIVA, Clovis.Elasticsearch: entenda a teoria por trás do mecanismo de busca textual.In: medium.com.2020; Disponível em: [https://medium.com/tentando-ser-um-unic%C3%B3rnio/elasticsearch-entenda-a-teoria-por-tr%C3%A1s-do-mecanismo-de-busca-textual-86d11bd4f69d](https://medium.com/tentando-ser-um-unic%C3%B3rnio/elasticsearch-entenda-a-teoria-por-tr%C3%A1s-do-mecanismo-de-busca-textual-86d11bd4f69d). Acesso em: 22 fev. 2023. 

[RICARDO, Baeza-Yates; BERTHIER, Ribeiro-Neto. Modern information retrieval: the concepts and technology behind search. New Jersey, USA: Addi-son-Wesley Professional, 2011.]Disponível em: [https://www.researchgate.net/publication/220688488_Modern_Information_Retrieval_the_Concepts_and_Technology_Behind_Search](https://www.researchgate.net/publication/220688488_Modern_Information_Retrieval_the_Concepts_and_Technology_Behind_Search). Acesso em: 22 fev. 2023. 
***