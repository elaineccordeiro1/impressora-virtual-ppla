# 🏷️ Impressora Virtual PPLA

Simulador de impressora térmica de etiquetas para a linguagem **PPLA** (Argox / Datamax DPL).
Cole o spool de impressão (`.lst`) e visualize a etiqueta renderizada no navegador — **incluindo o
QR Code real, escaneável direto na tela** — sem gastar etiqueta física.

## Por que existe

Durante a migração do código de barras de etiquetas industriais (Code 128 → QR Code) em um ERP,
não havia nenhuma ferramenta para pré-visualizar PPLA — o conhecido
[Labelary](https://labelary.com) só renderiza ZPL (Zebra). Cada ajuste de layout exigia imprimir
uma etiqueta de verdade. Este simulador resolve isso.

## Funcionalidades

- **Parser de registros PPLA**: texto (fontes escaláveis), linhas separadoras, código de barras
  Code 128 (`e`), QR Code (`W1d`), imagens (`Y`) e comandos de sistema (`STX`/`SOH`)
- **Codificador QR implementado do zero** em JavaScript puro (byte mode, ECC nível M,
  versões 1–3, Reed-Solomon sobre GF(256)) — validado por teste de ida e volta com verificação
  do código corretor; o QR renderizado é lido por qualquer leitor 2D ou câmera de celular
- **Renderização em escala real** (203 dpi), com régua em milímetros, rotação 90°,
  ancoragem de texto pela linha de base (comportamento real da impressora, verificado
  contra etiquetas físicas)
- **Inspetor de registros**: cada linha do spool interpretada com tipo, posição e conteúdo;
  tooltip em cada elemento da etiqueta mostra o registro de origem
- Tema claro/escuro, 100% client-side, **zero dependências** — um único arquivo HTML

## Como usar

Abra o `index.html` no navegador (ou acesse via GitHub Pages). Cole o conteúdo do arquivo
de spool na caixa à esquerda e clique em **Renderizar etiqueta**. Um exemplo de spool já
vem carregado.

## Limitações

- Fontes e espessuras são aproximações das fontes internas da impressora
- Imagens baixadas para a impressora (registros `ICP`) aparecem como marcador de posição
- Coordenadas assumem rotação 4 (layout retrato girado), o caso comum em etiquetas industriais

## Stack

HTML + CSS + JavaScript puro. Sem build, sem dependências, sem servidor.

<img width="1272" height="538" alt="image" src="https://github.com/user-attachments/assets/dff01b08-fbe7-4ef6-b478-be2450de4418" />

