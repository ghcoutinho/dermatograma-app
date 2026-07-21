# Dermatograma — Canídeos Silvestres - Gustavo Henrique Coutinho

Aplicativo de campo para a ficha **Dados clínicos e coleta de amostras** do projeto
*Dermatopatias em Canídeos Silvestres* (Doutorado em Patologia Animal — UFMG).

Funciona **100% offline** depois do primeiro acesso. Não envia nada para servidor
nenhum: todos os dados ficam no próprio aparelho.

## O que faz

- Ficha completa em 4 etapas: identificação, dados clínicos, material biológico e informações adicionais.
- **Dermatograma interativo** com as 42 regiões numeradas do lobo-guará; cada região registra
  várias lesões, cada uma com intensidade, distribuição e % de acometimento.
- **Fotos por região**, tiradas na hora ou escolhidas da galeria (redimensionadas automaticamente).
- **GPS** com preenchimento do município sem internet (base de 316 municípios do ES e divisas).
- **ID automático** do animal: espécie + local + sarna + sequência.
- Planilha **Excel única** acumulando todos os animais, exportação das fotos em ZIP e
  **PDF com 15 etiquetas de 50 × 30 mm**.

## Como publicar (GitHub Pages)

O GPS só funciona em endereço **HTTPS** — por isso a publicação. São 4 passos:

1. Crie um repositório **público** no GitHub, por exemplo `dermatograma-app`.
2. Envie o conteúdo desta pasta:
   ```bash
   git remote add origin https://github.com/SEU-USUARIO/dermatograma-app.git
   git branch -M main
   git push -u origin main
   ```
   *(ou use "Add file → Upload files" no site do GitHub e arraste todos os arquivos)*
3. No repositório: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `(root)` → Save**.
4. Em cerca de um minuto o link fica no ar:
   `https://SEU-USUARIO.github.io/dermatograma-app/`

## Como instalar no celular

1. Abra o link no **Chrome** (Android) ou **Safari** (iPhone).
2. Menu do navegador → **Adicionar à tela inicial** / **Instalar aplicativo**.
3. Abra pelo ícone. Na primeira vez que tocar em **📍 Obter**, autorize a localização.

Depois disso o app abre sem internet, inclusive em modo avião.

## Arquivos

| Arquivo | Função |
|---|---|
| `index.html` | O aplicativo inteiro (HTML + CSS + JS + ilustração embutida) |
| `sw.js` | Service worker — guarda o app em cache para uso offline |
| `manifest.webmanifest` | Permite instalar na tela inicial |
| `icon-*.png` | Ícones do app |
| `.nojekyll` | Impede o GitHub Pages de processar os arquivos |

## Onde ficam os dados

| Dado | Onde |
|---|---|
| Animais, locais, usuários | `localStorage` do navegador |
| Fotos | `IndexedDB` (comporta muito mais que o `localStorage`) |

> **Atenção:** limpar os dados do site pelo navegador apaga tudo.
> Exporte a planilha e o ZIP de fotos com regularidade.

## Atualizando o app

Ao substituir o `index.html`, altere também a versão do cache na primeira linha do
`sw.js` (`const CACHE = "derma-v10"` → `"derma-v11"`). Sem isso os aparelhos
continuam abrindo a versão antiga guardada em cache.
