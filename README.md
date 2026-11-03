# 📦 Controle de Estoque

App web (HTML, CSS e JavaScript puros, sem servidor) para controlar estoque pelo celular ou computador.

## Funcionalidades

- **Cadastro** de produtos com várias fotos (o **+** abre a câmera de novo), preço de **varejo**, preço de **atacado** e quantidade.
- O catálogo usa só a 1ª foto (capa); o cadastro guarda todas.
- **Aba Produtos**: tabela com foto, quantidade (+/−), valor, e botões Editar e Excluir.
- **Exportar Excel**: aba *Estoque* (com fotos e fórmulas) e aba *Atualizações* (histórico de entradas, saídas e edições).
- **Catálogo em PDF** com os produtos selecionados.
- **Flyer** (PNG ou PDF) com os produtos selecionados; textos e cores podem ser criados por IA.
- **Aba Adm** (login): valor pago, margem de lucro, fornecedor e contato, edição na própria tela e Excel do administrador.

## Como usar

Abra o `index.html` no navegador ou, para testar com um servidor local:

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```

## Publicar no GitHub Pages

```bash
git init
git add .
git commit -m "Controle de estoque"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/estoque-app.git
git push -u origin main
```

No GitHub: **Settings → Pages → Build and deployment → Deploy from a branch → `main` / `/ (root)`**. O endereço será `https://SEU-USUARIO.github.io/estoque-app/`.

## Configuração

### Senha do administrador

O padrão é usuário `adm` e senha `trocar123`. **Troque antes de publicar:**

1. Abra `gerar-senha.html` no navegador, digite o usuário e a senha desejados e copie o código gerado.
2. Cole o código em `ADM_HASH`, no arquivo `config.js`.

### Flyer com IA (opcional)

No modal do flyer, informe uma chave de API da Anthropic. Ela fica salva só no navegador (localStorage) e é enviada diretamente para a API. Sem chave, o flyer usa um modelo automático com cores sorteadas. O modelo pode ser trocado em `config.js` (`AI_MODEL`).

## Dados da loja e assinatura

O rodapé do app, o PDF (em todas as páginas) e o flyer trazem o WhatsApp, o endereço (com link para o Google Maps) e a assinatura "Desenvolvido por Maicon da Rosa Gonçalves". Os valores padrão estão no `index.html` (constante `BZ`). Para trocar sem mexer no código, acrescente em `config.js`:

```js
BIZ: { whats: '55DDDNUMERO', whatsTxt: '(DD) NNNN-NNNN', addr: 'Seu endereço', maps: 'https://www.google.com/maps/search/?api=1&query=...' }
```

## Limitações e segurança

- Os dados ficam no **navegador do aparelho** (IndexedDB), sem criptografia e sem sincronizar entre aparelhos. Exporte o Excel de vez em quando como cópia de segurança.
- O login do administrador roda no navegador. O código do app é público, então ele **não é segurança forte**: serve para esconder a aba de uso casual, não para barrar alguém determinado.
- Não coloque dados sensíveis reais em um repositório público.
- Use uma chave de API apenas em aparelhos de confiança. Ela fica visível para quem tiver acesso ao navegador.

## Tecnologias

[ExcelJS](https://github.com/exceljs/exceljs) (planilhas) e [jsPDF](https://github.com/parallax/jsPDF) (PDF), carregados via CDN.

## Licença

MIT. Veja `LICENSE` (preencha seu nome).
