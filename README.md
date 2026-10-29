# 👑 Sorteador de Times

Página única, sem build e sem dependências, para montar times a partir de uma lista de nomes.
Funciona offline depois de carregada e pode ser instalada no celular como atalho.

![Sorteador de Times](og-image.png)

---

## O que ela faz

- Duplas, trios, quartetos ou quintetos.
- Quantidade de times calculada automaticamente — ou fixada por você nos botões `+` / `−`.
- Quem sobra vira **time menor** ou **reserva**, à sua escolha.
- Remove nomes repetidos automaticamente.
- Botão para copiar o resultado pronto para colar no WhatsApp.
- Guarda a última lista no navegador de quem usa (nada é enviado para servidor nenhum).

---

## Arquivos do repositório

| Arquivo | Para que serve |
|---|---|
| `index.html` | O site inteiro: HTML, CSS e JavaScript em um arquivo só |
| `favicon.svg` | Ícone da aba do navegador |
| `icon-192.png`, `icon-512.png`, `icon-512-maskable.png` | Ícones de instalação no celular |
| `manifest.webmanifest` | Permite "Adicionar à tela de início" |
| `og-image.png` | Imagem que aparece ao compartilhar o link |
| `.nojekyll` | Impede o GitHub Pages de processar os arquivos |
| `.gitignore` | Evita subir lixo do sistema e do editor |
| `LICENSE` | Licença MIT |

---

## Publicar no GitHub Pages — passo a passo

### 1. Criar o repositório

1. Entre em [github.com/new](https://github.com/new).
2. **Repository name:** `sorteador-de-times`
3. Marque **Public** (o GitHub Pages gratuito exige repositório público).
4. **Não** marque "Add a README file" — você já tem um.
5. Clique em **Create repository**.

✅ **Checkpoint:** você deve estar numa página com o título do repositório e instruções de `git push`.

### 2. Subir os arquivos

**Opção A — pelo site, sem instalar nada (mais simples):**

1. No repositório recém-criado, clique em **uploading an existing file**.
2. Arraste **todos** os arquivos desta pasta para a área de upload.
3. Em "Commit changes", escreva `primeira versão do sorteador` e clique em **Commit changes**.

> ⚠️ O arquivo `.nojekyll` começa com ponto e pode ficar invisível no seu computador.
> No Windows: Explorador → aba **Exibir** → marque **Itens ocultos**.
> No Mac: `Cmd + Shift + .` dentro do Finder.

**Opção B — pelo terminal:**

```bash
cd caminho/para/sorteador-de-times

git init
git add .
git commit -m "primeira versão do sorteador"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/sorteador-de-times.git
git push -u origin main
```

✅ **Checkpoint:** atualize a página do repositório no GitHub. Você deve ver `index.html` na lista de arquivos.

### 3. Ligar o GitHub Pages

1. No repositório, abra **Settings** (engrenagem no topo).
2. No menu da esquerda, clique em **Pages**.
3. Em **Source**, escolha **Deploy from a branch**.
4. Em **Branch**, selecione **main** e a pasta **/ (root)**.
5. Clique em **Save**.

✅ **Checkpoint:** recarregue a página depois de 1 a 2 minutos. Aparece uma faixa verde com
`Your site is live at https://SEU-USUARIO.github.io/sorteador-de-times/`.

### 4. Testar

1. Abra o endereço no celular e no computador.
2. Cole 10 nomes, escolha **Trios** e clique em **Sortear Times**.
3. Confira: 4 times (3 + 3 + 2 + 2, ou 3 completos + 1 reserva se você escolheu "Deixar como reserva").
4. Clique em **Copiar resultado** e cole no WhatsApp.

✅ **Checkpoint final:** os times aparecem, o ícone 👑 está na aba do navegador e o link compartilhado
no WhatsApp mostra a imagem de prévia.

> ⏱️ Se o site não abrir de primeira, espere mais 2 minutos. O primeiro deploy do Pages demora.
> Se aparecer **404**, confira em Settings → Pages se a branch está em `main` e a pasta em `/ (root)`.

---

## Atualizar o site depois

Qualquer alteração em `index.html` vai ao ar sozinha, 1 a 2 minutos após o push:

```bash
git add .
git commit -m "descreva o que mudou"
git push
```

> Se a alteração não aparecer no navegador, force a recarga: `Ctrl + Shift + R`
> (no Mac, `Cmd + Shift + R`). O navegador guarda a versão antiga em cache.

---

## Usar domínio próprio (opcional)

1. Crie um arquivo chamado `CNAME` na raiz do repositório, com uma única linha: `sorteador.seudominio.com.br`.
2. No painel de DNS do domínio, crie um registro **CNAME** apontando `sorteador` para `SEU-USUARIO.github.io`.
3. Em Settings → Pages, preencha **Custom domain** com o mesmo endereço e marque **Enforce HTTPS**.

> O DNS pode levar algumas horas para propagar. Se você não administra o DNS do domínio,
> peça esse registro a quem administra.

---

## Rodar localmente

Basta abrir o `index.html` com dois cliques. Para testar o manifest e os ícones como num servidor real:

```bash
python3 -m http.server 8000
# abra http://localhost:8000
```

---

## Privacidade

Nenhum dado sai do navegador. A lista de jogadores fica salva apenas no `localStorage`
do aparelho de quem usa e é apagada pelo botão **Limpar Tudo**.
A única requisição externa é a fonte do Google Fonts.

---

## Licença

MIT — veja [LICENSE](LICENSE).
