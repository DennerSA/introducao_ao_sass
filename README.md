# 🌟 Introdução ao SASS

## 🗂️ Mapa Mental do Curso

### Aula 1 - **O que é SASS?** 🎯
- **Definição:**
  - O SASS é um _pre-processador_ de CSS.
  - Permite o uso de:
    - **Variáveis** 🎨
    - **Funções** ⚙️
    - Outros recursos para facilitar a escrita de estilos para páginas web.

- **Pré-requisitos:**
  1. Instalar uma versão do **Node.js**.
  2. Usar o **npm** para instalar o SASS:
     ```bash
     npm install -g sass
     ```

- **Atividades realizadas:**
  - Configuramos o ambiente de desenvolvimento.
  - Instalamos as dependências necessárias para usar o SASS no decorrer do curso.

---

### Aula 2 - **Sintaxes do SASS** ✍️

- **Tipos de Sintaxe no SASS:**
  - **SASS**:
    - Sintaxe mais antiga.
    - Não utiliza `{}` (chaves) ou `;` (ponto e vírgula).
  - **SCSS**:
    - **Sintaxe mais usada e convencional**.
    - Muito próxima ao CSS, utiliza `{}` e `;`.

- **Exemplo prático:**
  - Criamos dois arquivos para demonstrar as diferenças:
    - `exemplo.sass`
    - `exemplo.scss`

- **Como funciona o SASS?**
  - Como _pre-processador_, o SASS transforma o código em CSS.
  - Este processo é feito via linha de comando, dentro de um projeto Node.js.

- **Passo a passo para configurar e usar o SASS:**
  1. Criar um projeto Node.js:
     ```bash
     npm init -y
     ```
  2. Instalar o SASS como dependência de desenvolvimento:
     ```bash
     npm install sass --save-dev
     ```
  3. Configurar o comando no `package.json`:
     - Existem duas abordagens:
       1. **Mais flexível (manual)**:
          - Configurar o script apenas com o comando `sass`:
            ```json
            "scripts": {
              "sass": "sass"
            }
            ```
          - Ao rodar o comando, especifique manualmente os arquivos de entrada e saída:
            ```bash
            npm run sass src/main.scss dist/main.css
            ```
       2. **Mais automatizado (fixo)**:
          - Configurar o script com os arquivos de entrada e saída já definidos:
            ```json
            "scripts": {
              "sass": "sass src/main.scss dist/main.css"
            }
            ```
          - Ao rodar:
            ```bash
            npm run sass
            ```
            O arquivo `src/main.scss` será automaticamente transformado em `dist/main.css`.

- **Vantagens das abordagens:**
  - **Flexível**:
    - Ideal para projetos que têm múltiplos arquivos `.scss` e precisam de compilações específicas.
  - **Automatizado**:
    - Perfeito para projetos com um fluxo fixo e previsível.

- **Nota sobre dependências de desenvolvimento:**
  - Instalar o SASS como dependência de desenvolvimento garante que plataformas como a **Vercel** instalem o SASS automaticamente ao construir o projeto.

---

## 📌 Notas Finais
- Aprendemos sobre as duas sintaxes do SASS e sua aplicação.
- Exploramos diferentes abordagens para configurar scripts no `package.json`:
  - Manual para flexibilidade.
  - Automatizado para praticidade.
- Criamos um processo automatizado para transformar SCSS em CSS. 🚀

### Aula 3 - **Praticando com SASS** 🛠️

- **Reestruturação do projeto**:
  - Organizamos o projeto em:
    - **Pasta `source`**: Onde todo o desenvolvimento será feito.
    - **Pasta `build`**: Destinada aos arquivos processados para produção.
  - Tornamos o projeto mais profissional, excluindo arquivos desnecessários.

- **Vantagens do SASS**:
  - Permite escrever CSS de forma mais **rápida e otimizada**.
  - **Reutilização com variáveis**:
    - Declaramos variáveis usando `$nomeDaVariavel`, que podem ser aplicadas em qualquer regra.

    **Exemplo prático:**
    ```scss
    $corPrincipal: #eee;

    body {
        background-color: $corPrincipal;
    }

    header {
        background-color: $corPrincipal;

        h1 {
            color: red;
        }
    }
    ```

    - Comparado ao CSS tradicional:
      ```css
      body {
        background-color: #eee;
      }

      header {
        background-color: #eee;
      }
      header h1 {
        color: red;
      }
      ```

  - **Encapsulamento de regras**:
    - Facilita a hierarquia e organização de seletores.

  - **Melhoria no uso de pseudo-seletores e classes**:
    - O uso do `&` permite uma sintaxe mais limpa e menos repetitiva.
    
    **Exemplo:**
    ```scss
    $corPrincipal: #eee;
    $corSecundaria: #111;

    button {
        padding: 16px;
        background-color: $corSecundaria;
        color: $corPrincipal;

        &:hover {
            background-color: yellow;
        }
    }
    ```
    - Comparado ao CSS tradicional:
      ```css
      button {
        padding: 16px;
        background-color: #111;
        color: #eee;
      }
      button:hover {
        background-color: yellow;
      }
      ```

- **Automatizando com `--watch`**:
  - No `package.json`, atualizamos o script do SASS para incluir a flag `--watch`:
    ```json
    "scripts": {
      "sass": "sass source/main.scss build/main.css --watch"
    }
    ```
  - Assim, o SASS **monitora as alterações automaticamente** e compila os arquivos, sem precisar rodar o comando manualmente a cada vez.

- **Resumo da aula**:
  - Aprendemos a usar variáveis e encapsulamento no SASS.
  - Vimos como o SASS organiza o código, tornando-o mais limpo e menos repetitivo.
  - Automatizamos o processo de compilação para maior eficiência no desenvolvimento.

 ### Aula 4 - **Modularizando o código com SASS** 🔄

- **Modularização de código com SASS**:
  - O SASS permite **modularizar** o código, o que ajuda a dividir arquivos grandes em módulos menores, tornando o projeto mais organizado e facilitando a manutenção.

- **Exemplo prático**:
  - Criamos um arquivo **`reset.scss`** para aplicar regras de **reset** que serão reutilizadas em outros arquivos:
    ```scss
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
      font-family: sans-serif;
    }
    ```

- **Reutilizando o código modularizado**:
  - No arquivo **`main.scss`**, usamos o comando `@use` para importar o conteúdo do arquivo `reset.scss`:
    ```scss
    @use 'reset';

    body {
      background-color: #fff;
    }
    ```

- **Importante**:
  - Ao usar o `@use`, não precisamos referenciar a extensão `.scss` e o código do arquivo **`reset.scss`** é aplicado automaticamente no nosso `main.scss`.

- **Resumo da aula**:
  - Aprendemos como modularizar o código utilizando o `@use`.
  - Facilitamos a reutilização de estilos em nosso projeto, tornando-o mais organizado e escalável.

### Aula 5 - **Mixin: Reutilização de Propriedades CSS** ♻️  

- **Introdução ao `@mixin`**:  
  - O `@mixin` é uma funcionalidade do SASS que permite **reutilizar propriedades CSS** em vários locais, evitando duplicidade de código e tornando o CSS mais limpo e eficiente.  

- **Exemplo prático de criação de um `@mixin`**:  
  - Criamos um novo projeto para entender e praticar o uso de mixins.  
  - O exemplo abaixo mostra como criamos um `@mixin` chamado **`elementoForm`**, que aplica um conjunto de estilos reutilizáveis:  
    ```scss  
    @mixin elementoForm() {  
        padding: 8px;  
        display: block;  
        width: 100%;  
        margin-bottom: 16px;  
    }  
    ```  

- **Usando o `@mixin` no projeto**:  
  - Aplicamos o `@mixin` em diferentes elementos do formulário:  
    ```scss  
    form {  
        width: 100%;  
        max-width: 480px;  
        margin-top: 40px;  
        
        input {  
            @include elementoForm();  
            background-color: transparent;  
            border: none;  
            border-bottom: 1px solid #000;  
        }  

        button {  
            @include elementoForm();  
        }  
    }  
    ```  

- **Mixin com parâmetros**:  
  - O `@mixin` também pode receber **parâmetros** para tornar a reutilização ainda mais flexível.  
  - Por exemplo, poderíamos criar um mixin com parâmetro para configurar a **cor de fundo**:  
    ```scss  
    @mixin elementoForm($bgColor: transparent) {  
        padding: 8px;  
        display: block;  
        width: 100%;  
        margin-bottom: 16px;  
        background-color: $bgColor;  
    }  
    ```  
  - E utilizá-lo assim:  
    ```scss  
    input {  
        @include elementoForm(#f0f0f0);  
    }  
    ```  

- **Resumo da aula**:  
  - Aprendemos a criar e utilizar o `@mixin` para evitar duplicidade de código.  
  - Exploramos a utilização de mixins com e sem parâmetros, tornando o CSS mais organizado e reutilizável.  


### Aula 6 - **Funções no SASS** 🛠️  

- **Introdução às funções no SASS**:  
  - O SASS permite criar **funções personalizadas** para realizar cálculos ou manipulações reutilizáveis em qualquer parte do código.  
  - As funções são declaradas com `@function` e podem incluir lógica personalizada.  

- **Exemplo prático de função personalizada**:  
  - Criamos uma função chamada **`pixelParaEm`**, que converte um valor em pixels para **em**:  
    ```scss  
    @function pixelParaEm($alvoEmPixel, $contextoEmPixel: 16px) {  
        @return math.div($alvoEmPixel, $contextoEmPixel) + em;  
    }  
    ```  

  - Exemplo de uso da função no código:  
    ```scss  
    h2 {  
        font-size: pixelParaEm(48px);  
        text-align: center;  
    }  
    ```  

- **Funções nativas do SASS**:  
  - Além das funções personalizadas, o SASS oferece **funções nativas** para manipulação de cores e outros valores.  
  - Dois exemplos destacados nesta aula:  
    - **`darken($color, $amount)`**: Escurece uma cor.  
    - **`lighten($color, $amount)`**: Clareia uma cor.  

  - Exemplos de uso:  
    ```scss  
    $corPrimaria: #3498db;  

    header {  
        background-color: darken($corPrimaria, 10%);  
        color: lighten($corPrimaria, 20%);  
    }  
    ```  

- **Módulo `math`**:  
  - Utilizamos o módulo **`math`** para realizar operações matemáticas com precisão, garantindo consistência nos cálculos dentro do SASS.  

- **Resumo da aula**:  
  - Aprendemos a criar funções personalizadas para resolver problemas específicos no CSS, como conversões.  
  - Exploramos as funções nativas para manipulação de cores, como `darken` e `lighten`.  
  - Utilizamos o módulo `math` para cálculos matemáticos.  
