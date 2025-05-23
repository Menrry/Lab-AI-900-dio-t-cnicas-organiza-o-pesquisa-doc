# 🧪 Lab: Organização e Pesquisa de Documentos com IA

---

## 🎯 Objetivo do Laboratório

Este laboratório visa fornecer uma compreensão sólida sobre como **ferramentas de inteligência artificial** podem ser utilizadas para **organizar, minerar e extrair conhecimento** de grandes volumes de informação. Através de um processo prático de ingestão de dados, indexação e exploração, você desenvolverá habilidades essenciais para aplicar técnicas de organização e pesquisa de documentos baseadas em IA.
Este laboratório prático tem como objetivo demonstrar como utilizar **serviços de Inteligência Artificial da Azure** para organizar, indexar e permitir a pesquisa eficiente de documentos. Você aprenderá a ingerir dados, criar índices inteligentes e explorar informações valiosas de grandes volumes de documentos, focando em:

* **Azure Storage Accounts:** Para armazenar seus documentos.
* **Azure AI Services (anteriormente Azure Cognitive Services):** Para extrair insights e enriquecer seus dados.
* **Azure AI Search (anteriormente Azure Cognitive Search):** Para indexar e pesquisar seus documentos com capacidades de IA.

---

## 🚀 Três Passos Principais

O laboratório será dividido em três fases interligadas, cada uma com seus objetivos específicos:

### 1. Ingestão de Conteúdo para IA

Nesta etapa, o foco é preparar e alimentar seus documentos brutos em um formato que seja compreensível e processável por ferramentas de IA.

* **Coleta de Dados:** Identificação e agregação de uma amostra de documentos (e.g., PDFs, TXT, DOCX, HTML, etc.). Sugestões de fontes podem incluir artigos científicos, notícias, relatórios técnicos ou documentos de um domínio específico.
* **Pré-processamento:** Limpeza e normalização dos dados. Isso pode incluir remoção de ruídos (cabeçalhos, rodapés), extração de texto de PDFs, tratamento de caracteres especiais e conversão para um formato padronizado (e.g., texto puro).
* **Engenharia de Features (Opcional):** Para casos mais avançados, pode-se explorar a extração de metadados dos documentos (autor, data, tipo, etc.) para enriquecer o processo de ingestão.

### Exemplo de ingestão de Conteúdo para IA

Nesta etapa, o objetivo é preparar e carregar seus documentos para um ambiente onde a IA da Azure possa acessá-los e processá-los.

* **Criação de Azure Storage Account:** Você configurará uma conta de armazenamento Blob Storage na Azure para hospedar seus documentos. Esta será a fonte dos seus dados.
    * **Exemplo Prático:** Crie um container (e.g., `documentos-lab-ia`) e carregue alguns arquivos de exemplo (e.g., PDFs, TXT, DOCX) que você deseja indexar. Pense em documentos sobre um tópico específico, como artigos de notícias, relatórios ou manuais.
* **Seleção de Conteúdo:** Escolha uma amostra de documentos (por exemplo, 5-10 arquivos) para serem processados. Certifique-se de que eles contenham texto significativo.

### 2. Criação de Índices Inteligentes

Aqui, transformaremos o conteúdo ingerido em um **índice pesquisável e otimizado por IA**, que permitirá consultas eficientes e relevantes.

* **Escolha da Ferramenta de Indexação:** Seleção de uma ferramenta de IA para indexação de documentos. Exemplos incluem:
    * **Elasticsearch (com plugins de NLP/vetorização):** Poderoso para busca full-text e estruturada.
    * **OpenSearch (com recursos de ML):** Alternativa open-source ao Elasticsearch.
    * **Bibliotecas Python como Faiss ou Annoy:** Para indexação de embeddings vetoriais, ideal para busca de similaridade semântica.
    * **Serviços de Nuvem (Azure Cognitive Search, AWS Kendra, Google Cloud Search):** Soluções gerenciadas com recursos avançados de IA.
* **Vetorização/Embeddings (se aplicável):** Geração de representações numéricas (embeddings) dos documentos usando modelos de linguagem (e.g., BERT, Sentence-Transformers). Isso permite a busca por similaridade semântica, onde a pesquisa retorna documentos com significado similar, não apenas palavras-chave exatas.
* **Configuração do Índice:** Definição dos campos do índice, tipos de dados e estratégias de análise de texto (tokenização, stemming, stopwords).

### Exemplo de Índices Inteligentes com Azure AI Search

Aqui, você construirá um índice pesquisável no Azure AI Search, utilizando as capacidades de IA para enriquecer os dados dos seus documentos.

* **Criação de Azure AI Search Service:** Provisione um serviço de Azure AI Search no portal da Azure.
* **Conectando ao Storage Account:** Dentro do seu serviço de AI Search, crie uma **fonte de dados (data source)** que aponta para o seu container no Azure Storage Account.
* **Criação de Skillset com Azure AI Services:** Esta é a parte mais "inteligente"! Você definirá um **skillset** que utiliza diferentes capacidades de IA da Azure AI Services para enriquecer seus documentos.
    * **Exemplo Prático de Skillset:**
        * **`OCR Skill`:** Para extrair texto de imagens dentro de PDFs (se seus documentos contiverem imagens com texto).
        * **`Language Detection Skill`:** Para identificar o idioma do documento.
        * **`Key Phrase Extraction Skill`:** Para extrair as frases-chave mais importantes de cada documento.
        * **`Entity Recognition Skill`:** Para identificar entidades como pessoas, locais e organizações.
        * **`Text Translation Skill` (Opcional):** Se você tiver documentos em diferentes idiomas e quiser normalizá-los.
    * **Criação de Azure AI Services Resource:** Para usar as skills acima, você precisará de um recurso de **Azure AI Services (ou recursos específicos como Text Analytics, Computer Vision)** e conectar a chave e o endpoint ao seu skillset no AI Search.
* **Criação de Índice e Indexador:** Defina o **esquema do seu índice**, mapeando os campos extraídos pelo skillset e pelo conteúdo original. Crie um **indexador** que orquestra a ingestão de dados da fonte para o índice, aplicando o skillset.
    * **Exemplo Prático:** Mapeie campos como `content` (o texto completo do documento), `keyPhrases`, `entities`, `language`, etc. Defina os campos como pesquisáveis (`searchable`), filtráveis (`filterable`), facetáveis (`facetable`), etc., conforme a necessidade de busca.
 
      
### 3. Exploração Prática dos Dados Organizados

Nesta fase, você interagirá com o índice criado, realizando consultas e analisando os resultados para extrair insights.

* **Consultas Básicas:** Realização de pesquisas por palavras-chave e frases para verificar a eficácia da indexação.
* **Consultas Avançadas:** Experimentação com consultas complexas, incluindo:
    * **Busca Semântica:** Utilizando embeddings para encontrar documentos por significado.
    * **Filtros e Agregações:** Filtrando resultados por metadados e agrupando informações para obter estatísticas.
    * **Sugestão e Autocompletar:** Implementação de funcionalidades para melhorar a experiência de busca.
* **Análise de Resultados e Insights:** Avaliação da relevância dos documentos retornados, identificação de padrões, tendências ou informações valiosas que seriam difíceis de encontrar manualmente.

### Exemplo de exploração Prática dos Dados Organizados

Nesta fase, você irá interagir com o índice criado, realizando consultas e analisando os resultados diretamente do portal da Azure ou via API/SDK.

* **Consultas no Portal da Azure:** Utilize o explorador de pesquisa no portal da Azure para testar seu índice.
    * **Exemplo Prático:**
        * Pesquisar por palavras-chave: `"inteligencia artificial"`
        * Pesquisar por frases-chave extraídas: `keyPhrases eq 'machine learning'`
        * Filtrar por idioma: `language eq 'pt'`
        * Combinar filtros e termos de busca: `search=cloud computing&$filter=entities/organization eq 'Microsoft'`
* **Análise de Resultados e Insights:** Observe como os resultados são retornados e como os campos enriquecidos (frases-chave, entidades) podem ajudar a refinar suas buscas e a extrair conhecimento.
    * **Insights:** Qual a frequência de certas frases-chave? Quais entidades são mais mencionadas? Como a IA ajudou a identificar documentos relevantes que uma busca simples por palavra-chave não encontraria?

---

## 🧩 Como Tudo Funciona (Explicando o Exemplo)

O fluxo de trabalho exemplificado com os serviços Azure é o seguinte:

1.  **Armazenamento (Azure Storage Account):** Seus documentos (PDFs, TXT, DOCX, etc.) são armazenados de forma segura em um **container de Blob Storage**. Pense nele como seu "depósito de documentos".

2.  **Início do Processo (Azure AI Search - Indexador):** O **Indexador** dentro do Azure AI Search é o "motor" que inicia o processo. Ele é configurado para "olhar" para o seu container de Storage e detectar novos ou modificados documentos.

3.  **Enriquecimento de Dados (Azure AI Search - Skillset & Azure AI Services):**
    * Quando um documento é detectado, o Indexador o envia para o **Skillset** configurado.
    * O Skillset é uma "coleção de habilidades" de IA. Cada "habilidade" é um serviço do **Azure AI Services** que executa uma tarefa específica.
    * Por exemplo:
        * Se seu PDF tem uma imagem com texto, a **OCR Skill** usa o serviço de Computer Vision para extrair esse texto.
        * A **Key Phrase Extraction Skill** usa o serviço de Text Analytics para identificar termos importantes.
        * A **Entity Recognition Skill** também usa Text Analytics para encontrar nomes de pessoas, lugares, organizações.
    * O resultado de cada skill é anexado ao documento original, enriquecendo-o com metadados e informações extraídas por IA.

4.  **Indexação (Azure AI Search - Índice):**
    * Após o enriquecimento pelo Skillset, o documento (agora com todo o seu conteúdo original e os insights da IA) é enviado para o **Índice** do Azure AI Search.
    * O Índice é como um "catálogo" otimizado para pesquisa. Ele armazena o conteúdo e os metadados em um formato que permite buscas rápidas e relevantes.
    * Os campos são definidos com propriedades como `searchable` (para busca de texto), `filterable` (para filtrar resultados), `facetable` (para criar "categorias" de busca), entre outros.

5.  **Pesquisa (Azure AI Search - API/Portal):**
    * Agora que seus documentos estão indexados e enriquecidos, você pode realizar **consultas**.
    * Você pode pesquisar por palavras-chave no conteúdo completo, mas também pode pesquisar e filtrar pelos metadados e insights extraídos pela IA (como frases-chave, entidades ou idiomas).
    * Isso permite uma **busca muito mais inteligente e contextual**, indo além da simples correspondência de palavras. Por exemplo, você pode buscar todos os documentos que mencionam "inteligência artificial" e foram escritos por "Microsoft", mesmo que "Microsoft" não esteja explicitamente no texto, mas sim como uma entidade reconhecida.

Em resumo, o Azure Storage guarda seus arquivos, o Azure AI Services "lê" e "entende" o conteúdo desses arquivos, e o Azure AI Search usa esse entendimento para criar um índice super-pesquisável que te permite encontrar informações de forma eficiente e inteligente!

---
