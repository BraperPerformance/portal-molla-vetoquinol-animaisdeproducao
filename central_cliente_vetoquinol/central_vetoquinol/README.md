# Central do Cliente · Vetoquinol

Portal estático de documentos da Vetoquinol, desenvolvido pela Agência Molla. Reúne os planejamentos e relatórios de campanha em uma central de acesso com login para o cliente.

## Conteúdo

- **Planejamentos** — planos de mídia, cronogramas e estratégias (a preencher).
- **Relatórios** — relatórios de performance e análises de campanha.
  - Relatório da Live · Papo 90+ (YouTube, 13/07/2026), com comparativo entre as edições de 2023, 2024 e 2026.

O relatório abre embutido dentro do próprio portal, sem depender de arquivos externos.

## Estrutura do projeto

```
.
├── index.html      # Portal completo (login + central + relatório embutido)
├── vercel.json     # Configuração de deploy e headers
├── .gitignore
└── README.md
```

É um site estático de arquivo único: todo o HTML, CSS, JavaScript e o relatório (embutido em base64) estão dentro do `index.html`. Não há etapa de build nem dependências.

## Rodar localmente

Basta abrir o `index.html` no navegador. Se preferir servir via HTTP:

```bash
# Python
python3 -m http.server 8000

# ou Node
npx serve .
```

E acessar `http://localhost:8000`.

## Deploy no Vercel

### Opção A — via GitHub (recomendado)

1. Suba este repositório para o GitHub.
2. No [Vercel](https://vercel.com), clique em **Add New… → Project** e importe o repositório.
3. Em *Framework Preset*, selecione **Other** (é site estático, sem build).
4. Deixe *Build Command* e *Output Directory* em branco.
5. Clique em **Deploy**.

Cada `git push` na branch principal gera um novo deploy automático.

### Opção B — via CLI

```bash
npm i -g vercel
vercel        # deploy de preview
vercel --prod # deploy de produção
```

## Acesso

O portal é protegido por uma credencial de acesso do cliente, solicitada na tela de login.

> **Aviso de segurança.** Este é um site estático: a credencial é validada no próprio navegador e fica visível para quem inspecionar o código-fonte. A barreira serve para organizar e apresentar o material, **não** como proteção real de conteúdo confidencial. Para material sensível, hospede com autenticação de servidor (backend) — por exemplo, usando o [Vercel Password Protection](https://vercel.com/docs/security/deployment-protection) (planos pagos) ou uma solução equivalente.

## Atualizar documentos

Como o portal é um HTML de arquivo único com os documentos embutidos, adicionar novos arquivos (ex.: planejamentos) exige regenerar o `index.html` com o novo conteúdo embutido. Envie os arquivos ao responsável pela manutenção do portal para incluí-los na categoria correspondente.

---

© 2026 Agência Molla · Todos os direitos reservados.
