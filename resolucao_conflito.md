# Resolução de Conflitos no Git

Este documento descreve como identificar e resolver conflitos de merge no Git.

---

## O que é um conflito?

Um conflito ocorre quando duas branches alteram as **mesmas linhas** de um arquivo de maneiras diferentes. O Git não consegue decidir automaticamente qual versão manter, então pede para o desenvolvedor resolver manualmente.

---

## Quando conflitos acontecem?

- Ao fazer `git merge <branch>` quando ambas as branches editaram as mesmas linhas
- Ao fazer `git rebase` sobre uma branch que divergiu
- Ao fazer `git pull` quando o remoto e o local alteraram o mesmo trecho

---

## Como o Git marca um conflito

Quando há conflito, o Git insere marcadores no arquivo afetado:

```text
<<<<<<< HEAD
(sua versão na branch atual)
=======
(versão que veio da outra branch)
>>>>>>> origin/main
```

### Explicação dos marcadores:

| Marcador | Significado |
| -------- | ----------- |
| `<<<<<<< HEAD` | Início do trecho da sua branch atual |
| `=======` | Separador entre as duas versões |
| `>>>>>>> origin/main` | Fim do trecho da branch remota/outra |

---

## Passo a passo para resolver

### 1. Identificar os arquivos em conflito

```bash
git status
```

Os arquivos em conflito aparecem como **"both modified"**.

### 2. Abrir o arquivo e editar

Abra o arquivo no editor e escolha qual versão manter (ou combine as duas). **Remova todos os marcadores** (`<<<<<<<`, `=======`, `>>>>>>>`).

**Antes (com conflito):**
```text
<<<<<<< HEAD
O frete é calculado com base no CEP do destinatário.
=======
O frete é calculado com base no peso e dimensões do pacote.
>>>>>>> origin/main
```

**Depois (resolvido — combinando as duas versões):**
```text
O frete é calculado com base no CEP do destinatário, considerando também o peso e dimensões do pacote.
```

### 3. Marcar como resolvido e commitar

```bash
git add <arquivo_resolvido>
git commit -m "merge: resolve conflitos com main"
```

### 4. Fazer push

```bash
git push
```

---

## Dicas importantes

- **Sempre revise** as mudanças antes de commitar a resolução
- Use `git log --oneline --graph` para visualizar o histórico e confirmar que o merge ficou correto
- Prefira **commits pequenos e frequentes** para reduzir a chance de conflitos grandes
- Comunique-se com a equipe quando trabalhar nos mesmos arquivos
- Em caso de dúvida, use `git merge --abort` para cancelar o merge e voltar ao estado anterior

---

## Referências

- [Pro Git Book - Resolução de Conflitos](https://git-scm.com/book/pt-br/v2)
- [GitHub Docs - Resolving merge conflicts](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/addressing-merge-conflicts)
