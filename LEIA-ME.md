# Assistente Floripa Ticket — Guia de Instalação

## O que é isso?
Um chat de atendimento ao cliente com IA que aparece no canto do seu site.
Responde dúvidas sobre cancelamento, meia-entrada, ingresso não recebido e muito mais.

---

## PASSO 1 — Criar conta na Anthropic e pegar a chave de API

1. Acesse **console.anthropic.com**
2. Crie uma conta (pode usar Google)
3. Vá em **Billing** → adicione um cartão de crédito
4. Vá em **API Keys** → clique em **Create Key**
5. Dê o nome: `floripa-ticket-prod`
6. **Copie a chave imediatamente** — ela começa com `sk-ant-`
   ⚠️ Ela não aparece de novo depois de fechar a janela

---

## PASSO 2 — Subir o projeto na Vercel

1. Acesse **vercel.com** e faça login na sua conta
2. Clique em **Add New Project**
3. Clique em **"Import Git Repository"** → se não tiver repositório, use a opção **"Deploy from your computer"** ou arraste a pasta do projeto
4. Na tela de configuração, antes de clicar em Deploy, clique em **Environment Variables**
5. Adicione a variável:
   - **Name:** `ANTHROPIC_API_KEY`
   - **Value:** sua chave `sk-ant-...` que você copiou
6. Clique em **Deploy**
7. Aguarde o deploy terminar (1-2 minutos)
8. Copie a URL do seu projeto — vai ser algo como: `https://floripa-ticket-widget.vercel.app`

---

## PASSO 3 — Atualizar a URL no widget

1. Abra o arquivo `public/widget.js`
2. Na primeira linha após a abertura da função, você vai ver:
   ```
   const API_URL = 'https://SEU-PROJETO.vercel.app/api/chat';
   ```
3. Substitua `SEU-PROJETO` pela URL real do seu projeto na Vercel
4. Salve o arquivo
5. Volte na Vercel e faça um novo deploy (ou atualize o arquivo direto pelo painel)

---

## PASSO 4 — Instalar no WordPress

1. No painel do WordPress, vá em **Aparência → Editor de Temas** (ou use um plugin como **Header Footer Code Manager**)
2. Cole o código abaixo **antes do `</body>`** em todas as páginas:

```html
<script src="https://SEU-PROJETO.vercel.app/widget.js" defer></script>
```

Substitua `SEU-PROJETO` pela URL do seu projeto na Vercel.

**Alternativa mais fácil:** Instale o plugin **"Insert Headers and Footers"** no WordPress, cole o script acima na seção "Footer" e salve.

---

## PASSO 5 — Testar

1. Acesse seu site
2. O botão do Floripa Ticket vai aparecer no canto inferior direito
3. Clique e faça uma pergunta de teste: *"Como cancelo meu ingresso?"*

---

## Custos estimados

| Volume | Custo mensal estimado |
|--------|----------------------|
| Até 200 conversas | ~$1–3 USD |
| 200–500 conversas | ~$3–8 USD |
| 500+ conversas | ~$8–15 USD |

Você pode definir um limite de gasto mensal no console da Anthropic para nunca ter surpresa.

---

## Dúvidas?

Se travar em qualquer passo, manda mensagem no Claude que a gente resolve. 🎫
