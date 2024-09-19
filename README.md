# Playwright: Guia de Automação de Testes

## Sumário

- [O que é o Playwright?](#o-que-é-o-playwright)
- [Principais Características](#principais-características)
- [Instalando o Playwright](#instalando-o-playwright)
  - [No Windows](#no-windows)
  - [No Ubuntu/Linux](#no-ubuntulinux)
- [Configurando o Projeto](#configurando-o-projeto)
- [Escrevendo Testes no Playwright](#escrevendo-testes-no-playwright)
  - [Estrutura Básica de um Teste](#estrutura-básica-de-um-teste)
  - [Teste com Interações Mais Avançadas](#teste-com-interações-mais-avançadas)
- [Executando Testes no Playwright](#executando-testes-no-playwright)

---

## O que é o Playwright?

Playwright é um framework moderno de automação de testes para aplicações web, desenvolvido pela Microsoft. Ele é projetado para criar e executar testes de ponta a ponta (end-to-end) em várias plataformas e navegadores. O Playwright oferece uma API poderosa e flexível para interagir com a interface do usuário, garantindo que o seu software funcione conforme esperado em diferentes ambientes.

## Principais Características

- **Suporte a Múltiplos Navegadores**: Teste em navegadores como Chromium (Chrome e Edge), WebKit (Safari) e Firefox, garantindo uma ampla cobertura.
- **Automação Completa**: Simula ações do usuário (cliques, digitação, navegação) e verifica o conteúdo e estado dos elementos nas páginas.
- **Multilínguas**: Suporte a JavaScript, TypeScript, Python, C# e Java, proporcionando flexibilidade para equipes com diferentes habilidades.
- **Testes de Rede e Cookies**: Intercepta e modifica requisições de rede, manipula cookies e dados de armazenamento.
- **Captura de Tela e Vídeo**: Suporte integrado para capturas de tela e gravações de vídeo dos testes, facilitando a depuração de falhas.

---

## Instalando o Playwright

### No Windows

Pré-requisitos: **Node.js** e **npm** instalados.

1. Verifique se o Node.js e o npm estão instalados:
   ```bash
   node -v
   npm -v

2. Se não estiverem instalados, baixe o Node.js no site oficial:

**LTS**: Recomendado para a maioria dos usuários. <br>
**Current**: Inclui as versões mais recentes e recursos experimentais.

3. Após a instalação do Node.js, execute:
```bash
npm init playwright@latest
```
4. Verifique se o Playwright foi instalado corretamente:
```bash
npx playwright --version
```

### No Ubuntu/Linux

1. Verifique se o Node.js e o npm estão instalados:
```bash
   node -v
   npm -v
```

2. Se não estiverem instalados, execute no terminal:
```bash
sudo apt update
sudo apt install nodejs npm
```

3. Instale o Playwright:
```bash
npm init playwright@latest
```

5. Verifique a instalação:
```bash
npx playwright --version
```

### Configurando o Projeto
Após a instalação, o arquivo ```playwright.config.js``` é gerado para definir a configuração do Playwright.

Exemplo de playwright.config.js:
```javascript
// playwright.config.js
module.exports = {
  // Definir navegadores para testar
  projects: [
    { name: 'firefox', use: { browserName: 'firefox' } },
    { name: 'webkit', use: { browserName: 'webkit' } },
    { name: 'chromium', use: { browserName: 'chromium' } },
  ],
  
  // Configurações globais
  use: {
    baseURL: 'https://example.com',
    screenshot: 'on', // Captura de tela ao falhar
    video: 'on',      // Gravação de vídeo dos testes
  },

  // Executar testes em paralelo
  workers: 4,

  // Retries para testes que falham
  retries: 1,
};
```

### Escrevendo Testes no Playwright

**Estrutura Básica de um Teste**

Crie os arquivos de teste na pasta tests/ com a extensão .spec.js(no caso de se utilizar Javascript como linguagem). Cada arquivo pode conter vários casos de teste.

Exemplo Prático:
```javascript
// tests/example.spec.js
const { test, expect } = require('@playwright/test');

test('Validar o título da página inicial', async ({ page }) => {
  await page.goto('https://enacom.com');
  await expect(page).toHaveTitle('Enacom');
});
```
#### Teste com Interações Mais Avançadas

```javascript
// tests/advanced.spec.js
const { test, expect } = require('@playwright/test');

test('Fazer login e validar usuário', async ({ page }) => {
  // Acessar a página de login
  await page.goto('https://example.com/login');

  // Preencher campos de login
  await page.fill('#username', 'seu-usuario');
  await page.fill('#password', 'sua-senha');

  // Clicar no botão de login
  await page.click('button[type="submit"]');

  // Verificar se foi redirecionado para a página do usuário
  await expect(page).toHaveURL('https://example.com/dashboard');
  
  // Verificar se o nome do usuário está visível
  await expect(page.locator('h1')).toContainText('Bem-vindo, seu-usuario');
});
```

### Executando Testes no Playwright

1. Para executar todos os testes:
```bash
npx playwright test
```

2. Para gerar relatórios em HTML:
```bash
npx playwright test --reporter=html
```

3. Para executar testes em um navegador específico:
```bash
npx playwright test --project=firefox
```

4. Para executar testes no modo interativo com depuração:
```bash
npx playwright test --debug
```
5. Para visualizar os testes sendo executados em um navegador (headful mode):
```bash
npx playwright test --headed
```
