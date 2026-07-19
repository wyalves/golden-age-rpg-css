# Template de Postagem — Kamo Akihito · Manual de Uso (v1)

CSS hospedado: `https://jkga.wyalves.dev/akihito/template-posts.css`
Modelo-mestre: `akihito-exemplo.html` (duplique, edite, poste)

---

## 1. Cabeçalho — dois modos (escolha um)

### Modo Capa (com imagem)
```html
<div class="akh-cover" style="background-image:url('SUA_URL');"><div class="akh-cover-veil"><div class="akh-name">Kamo Akihito</div><div class="akh-epithet">加茂 秋人 — Grau 4 · Kyoto</div></div></div>
```
- Troque apenas a URL. A imagem é cortada para 220px de altura (150px no celular), centralizada, com véu escuro que a funde no fundo.
- **Hotlink**: Pinterest e afins às vezes bloqueiam visitantes. Se a capa sumir para os outros, hospede a imagem no fórum ou no seu domínio.

### Modo Enxuto (sem imagem)
```html
<div class="akh-lean"><div class="akh-name">Kamo Akihito</div><div class="akh-epithet">加茂 秋人 — Grau 4 · Kyoto</div></div>
```
- Só tipografia + tick oxblood sob o nome. Ideal para posts sociais, cenas curtas ou quando não há arte que valha a capa.

O **epíteto** (`akh-epithet`) é editável por post: dá pra trocar "Grau 4 · Kyoto" por qualquer coisa ("Missão: Colina Vermelha", uma data, um codinome).

---

## 2. Bloco de Cena — opcional

```html
<div class="akh-scene"><div class="akh-scene-title">Título do Post</div><div class="akh-scene-sub">Turno 03 · Local</div></div>
```
- Vai **entre o header e o corpo**.
- Título serif 22px + subtítulo mono miúdo, centralizados, com traço fino embaixo.
- **Para desativar: apague o bloco inteiro.** Nada mais precisa mudar.
- O subtítulo também é opcional — pode ficar só o título.

---

## 3. Corpo Narrativo — as quatro vozes

Tudo acontece dentro de `<div class="akh-body"> ... </div>`.

| Voz | Como escrever | Como renderiza |
|---|---|---|
| Narração | texto normal | pergaminho `#E7DFD8` |
| **Fala** | `<b>— Fala aqui</b>` | branco quente + negrito |
| *Pensamento* | `<i>Pensamento aqui</i>` | lilás vivo + itálico |
| Técnica | `<span class="akh-tech">Nome da Técnica</span>` | carmesim serifado, caixa alta, glow |

### Capitular (opcional)
Primeira letra gigante em oxblood, estilo abertura de capítulo:
```html
<span class="akh-drop">A</span> poeira ainda não tinha assentado...
```
Cole no comecinho do primeiro parágrafo (a letra fica dentro do span, o resto da palavra fora). Use com parcimônia — funciona melhor em posts longos/de abertura.

---

## 4. Imagens no Corpo

### Largura total
```html
<img class="akh-img" src="URL">
```
Corta em 300px de altura máx. (`object-fit:cover`), borda da paleta, leve dessaturação para assentar no tema.

### Lateral (texto contorna)
```html
<img class="akh-img-side" src="URL">
```
Flutua à direita com 42% da largura; o texto envolve. No celular vira largura total automaticamente.

### Legenda — opcional nas duas
```html
<img class="akh-img" src="URL"><span class="akh-img-cap">legenda aqui</span>
```
Mono miúdo centralizado. **Para não usar: simplesmente omita o span.**

### Regras de posicionamento (importante)
- Imagem (e legenda) **coladas** no parágrafo — sem Enter entre `</p>...texto` e `<img>`. A imagem full quebra linha sozinha (`display:block`).
- Padrão: `...fim do parágrafo.[LINHA EM BRANCO]<img ...><span class="akh-img-cap">...</span>Início do próximo parágrafo...`
- A lateral funciona melhor colada no **início** do parágrafo que vai contorná-la.
- Não empilhe duas laterais seguidas; alterne com texto ou use full-width.

---

## 5. Barras de Status

```html
<div class="akh-bar akh-hp"><span class="akh-lab">HP</span><span class="akh-track"><span class="akh-fill" style="width:91%"></span></span><span class="akh-val">1.201 / 1.320</span></div>
```
Dois números para editar por barra:
- `width:XX%` = **quanto está cheio** (HP em 60% → `width:60%`)
- `X / Y` = valor atual / máximo

Cores fixas por classe: `akh-hp` oxblood · `akh-ea` azul-aço · `akh-san` ouro. Uma barra pode ser removida apagando a `div` inteira dela (ex.: cena sem SAN em jogo).

---

## 6. Considerações

Estrutura: `<details class="akh-cons">` → meta → chips → subseções → legenda.

### 6.1 Meta (chave-valor)
```html
<div class="akh-kv akh-kv-wide"><span class="akh-kv-k">Objetivo</span><span class="akh-kv-v">Texto</span></div>
```
- `akh-kv` = célula normal; adicione `akh-kv-wide` para célula de largura dupla (use no Objetivo).
- Valores aceitam links (`<a href>`) — útil no Vigor apontando pro banco.
- Adicione ou remova células à vontade; a grade se reorganiza sozinha.

### 6.2 Chips de ação
```html
<span class="akh-chip akh-chip-hot">ATK <b>1/1</b></span>
```
- `akh-chip` = apagado (ação não usada) · `akh-chip` + `akh-chip-hot` = **aceso em oxblood** (ação gasta no turno).
- O toggle é só adicionar/remover `akh-chip-hot`. Semáforo instantâneo da economia de ações.

### 6.3 Subseções colapsáveis
```html
<details class="akh-sub"><summary>Nome da Seção</summary><div class="akh-sub-txt">conteúdo<br>mais conteúdo</div></details>
```
- As cinco padrão: **Resumo das Ações** (a mais importante — bullets do que o personagem fez), **Aptidões Usadas**, **Cálculos**, **Notas & Efeitos**, **Inventário** (obrigatório em raids, pela regra do fórum).
- **Todas são opcionais e independentes** — apague as que não se aplicam ao post (cena social não precisa de Cálculos), crie novas com o mesmo esqueleto.
- Dentro de `akh-sub-txt`, quebras de linha são **`<br>` explícitos** (não Enter!).
- Semântica interna das tags (diferente do corpo): `<b>` = valor em destaque · `<i>` = anotação apagada em cinza · `›` = marcador de item.
- Padrão de fórmula em Cálculos: `12 (Base) +3 (Franco-Atirador) = <b>15</b>`.
- Para uma subseção **já vir aberta**: `<details class="akh-sub" open>`.

### 6.4 Legenda
Rodapé fixo do painel, sempre visível quando as Considerações abrem. Já pronta; não precisa mexer. Removível se um dia quiser (apagar a `div class="akh-legend"`).

### Considerações inteiras já abertas
`<details class="akh-cons" open>` — útil em posts de combate onde o narrador vai direto ali. O padrão é fechado (post limpo).

---

## 7. Rodapé

```html
<div class="akh-sig"><span class="akh-links"><a href="...">Ficha</a> · <a href="...">Logs</a> · <a href="...">Banco</a></span></div>
```
Links já configurados no modelo-mestre. Dá pra adicionar um quarto link seguindo o padrão `· <a href>`.

---

## 8. Checklist por post (fluxo de 2 minutos)

1. Duplicar o `akihito-exemplo.html`
2. Header: escolher modo (capa → trocar URL / enxuto → trocar bloco)
3. Cena: editar título/subtítulo ou apagar o bloco
4. Corpo: escrever (Enter livre AQUI, e só aqui)
5. Imagens: inserir coladas nos parágrafos, legendas se quiser
6. Status: atualizar `width%` e `X / Y` das três barras
7. Considerações: meta → acender chips gastos → preencher/apagar subseções
8. Colar tudo no fórum e postar

---

## 9. Manutenção & Solução de Problemas

**Versionamento** — v1 está congelada. Ajustes cosméticos (cores, paddings) podem ir direto na URL atual sem quebrar posts antigos. Mudanças estruturais (classes novas incompatíveis) → publicar como `template-posts-v2.css` em URL nova e migrar só os posts futuros.

**Espaçamento fantasma apareceu** → há um Enter encostado numa tag estrutural. Compacte a linha.

**Template inteiro sem estilo** → o `@import` foi estrangulado pelo filtro do fórum ou o CSS saiu do ar. Teste trocar a primeira linha por `<link rel="stylesheet" href="https://jkga.wyalves.dev/akihito/template-posts.css">`.

**Capa não aparece para outros** → hotlink bloqueado pela origem da imagem. Re-hospede.

**Subseção não abre/fecha** → confira se o `<details>` fechou com `</details>` e se o `<summary>` é o primeiro filho.

**Barra transbordando** → `width` acima de 100% ou typo no valor.
