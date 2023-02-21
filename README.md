# SIR\_ChatGPT
Development of a Simple Informational Retrieval System obtaining guidance with ChatGPT. Tested on CISI collection with BM25 algorithm.

### Github do Projeto: 
<https://github.com/marcusborela/Sir-ChatGPT.git> 
### Autor: 
Marcus Vinícius Borela de Castro (<marcusborela@yahoo.com.br>) 

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
##
## Estudo prévio sobre ChatGpt 
Antes de iniciar o projeto assistido pelo ChatGPT, precisava me atualizar sobre suas capacidades e desejava descobrir algumas ferramentas de apoio. Por isso criei esta seção.

Perguntei ao ChatGPT “o que é ChatGPT”, e ele respondeu:

“ChatGPT é um modelo de linguagem de inteligência artificial criado pela OpenAI. Ele é projetado para conversar com usuários em linguagem natural, respondendo a perguntas, fornecendo informações e até mesmo fazendo pequenas conversas. O ChatGPT foi treinado em uma grande quantidade de dados de linguagem natural para aprender a entender a linguagem humana e gerar respostas relevantes e coerentes. Ele é capaz de conversar sobre uma ampla variedade de tópicos e pode ser usado em diversas aplicações, desde assistentes de bate-papo em sites até chatbots em redes sociais.”
### Recursos
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

### Extensões do Google  (em ordem de importância)
1. [WebChatGPT: ChatGPT com acesso à internet](https://chrome.google.com/webstore/detail/webchatgpt-chatgpt-with-i/lpfemeioodjbpieminkklglpmhlngfcn): permite busca informações atualizadas. Como o gpt-3 foi treinado em 2021, ele não traz respostas atualizadas (exemplo: quem é o presidente do Brasil?). Essa extensão permite que o chatgpt faça uma busca atualizada (configurável: período, número de resultados, etc) o que o torna ainda mais utilizável.
1. [YouTube Summary with ChatGPT](https://chrome.google.com/webstore/detail/youtube-summary-with-chat/nmmicjeknamkfloonkhhcjmomieiodli): gera sumário do vídeo no youtube
1. [FancyGPT](https://chrome.google.com/webstore/detail/fancygpt/meonalmakdjaojaoipfhahcfccoecegk?hl=pt-BR): salva como pdf, txt ou imagem (jpg).
1. [ChatGPT for Google](https://chrome.google.com/webstore/detail/chatgpt-for-google/jgjaeacdkonaoafenlfkkkmbaopkbilf): responde em pesquisas no google. Configurável, permite, por exemplo, apagar de forma automática os chats no openai.
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

[(relatório abaixo foi criado pelo ChatGPT ao final do diálogo que inclui a contextualização até a conclusão da fase de compreensão dos conceitos envolvidos no negócio)](https://github.com/marcusborela/Sir-ChatGPT/blob/main/docs/Desenvolvendo%20em%20conjunto%20com%20WebChatGPT/Contextualizacao%20e%20compreensao%20do%20negocio.md)


### Relatório Fase 1 - Compreensão do Negócio
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

$$R-Precision = \frac{\text{Número de documentos relevantes nos primeiros R resultados}}{R}$$

##### 1.4.6 NCG (Normalized Cumulative Gain)
A métrica NCG (Normalized Cumulative Gain) é utilizada para medir a eficácia de um sistema de recuperação de informação, levando em consideração a posição de cada item na lista de resultados. A métrica assume que as avaliações de relevância são binárias, ou seja, um item é relevante ou não relevante. A NCG normaliza a medida de ganho acumulado (CG) pelo ideal máximo de ganho acumulado (ICG), a fim de levar em conta o número de itens relevantes.

A fórmula da NCG é dada por:

$$NCG@k = \frac{CG@k}{ICG@k}$$

Onde:

- $CG@k$ é o ganho acumulado na posição $k$.
- $ICG@k$ é o ganho acumulado ideal na posição $k$.


O ganho acumulado ideal (ICG) na posição $k$ é calculado da seguinte forma:

$$ICG@k = \sum_{i=1}^k \frac{2^{rel_i} - 1}{\log_2(i+1)}$$

Onde:

- $rel_i$ é o nível de relevância do documento na posição $i$ (0 ou 1).


Por exemplo, se houver $n$ documentos relevantes, o ganho acumulado ideal nas primeiras $k$ posições seria:

$$ICG@k = \sum_{i=1}^k \frac{2^{rel_i} - 1}{\log_2(i+1)}$$
$$ICG@k = \frac{2^{rel_1} - 1}{\log_2(1+1)} + \frac{2^{rel_2} - 1}{\log_2(2+1)} + ... + \frac{2^{rel_n} - 1}{\log_2(n+1)}$$

O ganho acumulado (CG) na posição $k$ é dado por:

$$CG@k = \sum_{i=1}^k \frac{2^{rel_i} - 1}{\log_2(i+1)}$$

Assim, a métrica NCG varia de 0 a 1, onde valores mais próximos de 1 indicam um sistema mais eficaz na recuperação de informações relevantes.


***