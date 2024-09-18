## O que é o Playwright

Playwright é um framework moderno de automação de testes para aplicações web, desenvolvido pela Microsoft. Ele é projetado para criar e executar testes de ponta a ponta (end-to-end) em várias plataformas e navegadores. O Playwright oferece uma API poderosa e flexível para interagir com a interface do usuário, garantindo que o seu software funcione conforme esperado em diferentes ambientes.

## Quais as suas principais características?

- **Suporte a Múltiplos Navegadores**: O Playwright permite testar em vários navegadores, incluindo Chromium (Chrome e Edge), WebKit (Safari) e Firefox, garantindo uma ampla cobertura de testes.

- **Automação e Interação Completa**: Permite simular ações do usuário, como clicar, digitar e navegar, além de verificar o conteúdo das páginas e os estados dos elementos.

- **Testes Multi-Linguagem**: O Playwright suporta várias linguagens de programação, como JavaScript, TypeScript, Python, C#, e Java, proporcionando flexibilidade para equipes com diferentes expertise.

- **Testes de Rede e Cookies**: Oferece funcionalidades avançadas para interceptar e modificar requisições de rede, manipular cookies e armazenar dados para testar diferentes cenários.

- **Captura de Tela e Vídeo**: Possui suporte integrado para captura de screenshots e gravação de vídeos dos testes, facilitando a análise e depuração de falhas.


## Instalando o Playwright no Windows

A instalação é bem simples, basta seguir os passos abaixo:

Pré-requisitos:
- Ter o Node.js e o npm instalados

1. Instalação

Verificando se você possui o Node e o Npm instalados:
```javascript
node -v
```
```javascript
npm -v
```

**Caso não estejam instalados:**
1. Baixe o Instalador do Node.js

Primeiro, baixe o instalador do Node.js da <a href="https://nodejs.org/pt"></a>página oficial de downloads. Existem dois tipos de instaladores:

LTS (Long Term Support): Recomendado para a maioria dos usuários.
Current: Inclui as versões mais recentes e recursos experimentais.
Você pode escolher a versão que deseja e fazer o download do instalador .msi (para sistemas de 64 bits ou 32 bits, conforme necessário).

2. Siga os passos do instalador e verifique novamente os comandos da etapa '1. Instalação',

3. Realizadas as etapas anteriores, execute agora os comandos abaixo para instalar o Playwright

```javascript
npm init playwright@latest
```

4. Verificando se foi instalado corretamente
```javascript
npx playwright --version
```

## Instalando o Playwright no Ubuntu/Linux

1. Instalação

Verificando se você possui o Node e o Npm instalados:
```javascript
node -v
```
```javascript
npm -v
```

**Caso não estejam instalados:**

1. Execute o comando abaixo no terminal: 
```javascript
sudo apt update
```

2. Agora execute este comando:
```javascript
sudo apt install nodejs npm
```

3. Com o Node.js e o npm instalados, você pode instalar o Playwright e os navegadores necessários

```javascript
npm init playwright@latest
```

4. Verificando se foi instalado corretamente

```javascript
npx playwright --version
```

## Configurando o projeto

Um arquivo chamado playwright.config.js é criado assim que o projeto for instalado. Por meio dele poderemos fazer algumas modificações básicas. Por exemplo:

```javascript
// playwright.config.js
module.exports = {
  // Define os navegadores que serão utilizados
  projects: [
    { name: 'firefox', use: { browserName: 'firefox' } },
    { name: 'webkit', use: { browserName: 'webkit' } },
    { name: 'webkit', use: { browserName: 'chromium' } },
  ],
  
  // Define a URL base para os testes
  use: {
    baseURL: 'https://example.com',
    // Configura a captura de tela e gravação de vídeo
    screenshot: 'on',
    video: 'on',
  },
  
  // Configura o número de testes paralelos
  workers: 4,
  
  // Habilita o modo de depuração
  retries: 1,
};
```

## Como executar testes com o Playwright?

1. Escreva os seus casos de teste

Crie arquivos de teste em uma pasta apropriada, como por exemplo, 'Testes_Smoke/', e utlize a extensão desejada (ex: '.spec.js', '.test.js').

Abaixo, um exemplo prático de teste:

```javascript
// tests/example.spec.js
const { test, expect } = require('@playwright/test');

test('Identificar o título principal da página "Enacom"', async ({ page }) => {
  await page.goto('https://enacom.com');
  await expect(page).toHaveTitle('Enacom');
});
```

2. Executando os Testes

Utilize o comando:
```javascript
npx playwright test
```

Para executar outros testes em paralelo e visualizar relatórios detalhados, utilize:
```javascript
npx playwright test --reporter=html
```


