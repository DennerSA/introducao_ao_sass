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

