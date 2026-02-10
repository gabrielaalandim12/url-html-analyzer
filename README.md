# HtmlAnalyzer

## Visão geral

Este projeto implementa um programa em Java que analisa o conteúdo HTML de uma URL e identifica o trecho de texto localizado no nível mais profundo da estrutura de tags.

Quando mais de um trecho de texto estiver no mesmo nível máximo de profundidade, o primeiro encontrado é retornado.
Caso a estrutura do HTML seja inválida, o programa retorna a mensagem "malformed HTML".
Em caso de falha na conexão com a URL, o programa retorna a mensagem "URL connection error".

A solução foi desenvolvida utilizando apenas recursos nativos do JDK 17, respeitando as restrições definidas no desafio.

---

## Premissas consideradas

A implementação considera as seguintes premissas:

- O código HTML é dividido em linhas;
- Cada linha contém apenas um tipo de conteúdo: tag de abertura, tag de fechamento ou trecho de texto;
- Uma mesma linha não contém mais de um tipo de conteúdo;
- Apenas tags com abertura e fechamento são utilizadas;
- Tags de abertura não possuem atributos;
- Espaços de indentação e linhas em branco são ignorados.

---

## Requisitos funcionais

**RF1** – Ler o conteúdo HTML a partir de uma URL informada como argumento.

**RF2** – Identificar o nível de profundidade das tags HTML durante a leitura do documento.

**RF3** – Encontrar o trecho de texto localizado no nível mais profundo da estrutura HTML.

**RF4** – Retornar o primeiro trecho de texto encontrado no nível máximo de profundidade.

**RF5** – Identificar estruturas HTML malformadas e retornar a mensagem "malformed HTML".

**RF6** – Tratar falhas de conexão com a URL e retornar a mensagem "URL connection error".

---

## Requisitos técnicos

**RT1** – Implementar a solução como um programa Java executado via linha de comando, utilizando o JDK 17.

**RT2** – Não utilizar bibliotecas externas ao JDK.

**RT3** – Não utilizar classes ou pacotes relacionados à manipulação de HTML, XML ou DOM.

**RT4** – Permitir a compilação do programa por meio do comando:
`javac HtmlAnalyzer.java`

**RT5** – Permitir a execução do programa por meio do comando:
`java HtmlAnalyzer inserir-url-aqui`

**RT6** – Gerar exclusivamente os seguintes tipos de saída no console padrão:
* Trecho de texto identificado no HTML;
* Mensagem "malformed HTML";
* Mensagem "URL connection error".

**RT7** – Disponibilizar o código-fonte em arquivos `.java` e este arquivo `README.md`, compatíveis com **UTF-8**.

**RT8** – Preparar a entrega da solução em arquivo `.tar` ou `.tar.gz`, nomeado conforme o nome do(a) candidato(a), sem acentos e com espaços substituídos por underscore.

---

## Descrição da Solucão

O programa realiza a leitura do HTML linha por linha e utiliza uma **pilha** para controlar as tags abertas durante o processamento.

A profundidade de cada trecho de texto é determinada pela quantidade de tags abertas no momento da leitura. Sempre que um trecho de texto é encontrado em um nível mais profundo do que os anteriores, ele é armazenado como resultado.

A validação da estrutura do HTML é feita por meio da verificação da correspondência entre tags de abertura e fechamento. Caso seja identificada qualquer inconsistência, o HTML é considerado malformado.

---

## Execução

Exemplo de execução do programa:

```bash
java HtmlAnalyzer [https://hiring.axreng.com/internship/example1.html](https://hiring.axreng.com/internship/example1.html)
```

---

## Considerações finais

A solução foi projetada sob os princípios de **Clean Code** e eficiência algorítmica. A escolha da estrutura de dados **Stack (Pilha)** para o processamento das tags garante que a análise seja feita em tempo linear, garantindo performance mesmo em arquivos HTML extensos.

A implementação prioriza:
* **Robustez:** Tratamento de exceções de rede e malformação de tags.
* **Legibilidade:** Código autoexplicativo e estruturado.
* **Conformidade:** Estrita aderência aos requisitos técnicos (RT5 a RT8).
