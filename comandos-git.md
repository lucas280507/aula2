# Comandos Git

Este arquivo contém um guia rápido com comandos Git úteis para a disciplina e para o fluxo de trabalho em repositórios.

| Comando | Descrição |
| ------- | --------- |
| `git init` | Inicializa um repositório Git vazio no diretório atual |
| `git clone <url>` | Clona um repositório remoto para o computador local |
| `git status` | Mostra o estado atual da árvore de trabalho e do índice |
| `git add <arquivo>` | Adiciona arquivos ou mudanças ao staging area |
| `git commit -m "mensagem"` | Salva um snapshot das mudanças no histórico local |
| `git push` | Envia commits locais para o repositório remoto |
| `git pull` | Busca e integra mudanças do repositório remoto |
| `git branch` | Lista, cria ou deleta branches |
| `git checkout <branch>` | Troca para outra branch ou commit |
| `git merge <branch>` | Mescla outra branch na branch atual |
| `git log --oneline --graph` | Mostra histórico de commits de forma compacta e gráfica |
| `git diff` | Exibe diferenças entre arquivos, branches ou commits |
| `git reset --hard <hash>` | Reverte o estado local para um commit específico, removendo mudanças |
| `git revert <hash>` | Cria um novo commit que desfaz as mudanças de um commit anterior |
| `git remote -v` | Mostra os repositórios remotos configurados |

| `git stash` | Guarda mudanças temporariamente sem fazer commit |
| `git stash save "msg"` | Guarda mudanças com uma mensagem descritiva |
| `git stash list` | Lista todos os stashes salvos |
| `git stash apply` | Recupera o último stash (mantém no histórico) |
| `git stash pop` | Recupera o último stash e remove do histórico |
| `git stash apply stash@{n}` | Aplica um stash específico pelo índice |
| `git stash clear` | Remove todos os stashes salvos |
| `git checkout -b <branch>` | Cria e muda para uma nova branch |
| `git fetch origin` | Busca atualizações do remoto sem aplicar |
| `git rebase origin/main` | Reaplica commits da branch sobre a main atualizada |
| `git push --force-with-lease` | Força push de forma segura, verificando se o remoto não mudou |

## Uso recomendado

1. Edite arquivos.
2. Use `git status` para revisar o que mudou.
3. Adicione as mudanças com `git add`.
4. Faça o commit com `git commit -m "tipo: descrição"`.
5. Envie para o GitHub com `git push`.

---

## Convenções de Commits (Git Semântico)

| Tipo | Descrição |
| ---- | --------- |
| `feat` | Nova funcionalidade |
| `fix` | Correção de bug |
| `docs` | Alteração em documentação |
| `style` | Formatação, sem mudança de lógica |
| `refactor` | Refatoração, sem alterar comportamento externo |
| `test` | Adição ou modificação de testes |
| `build` | Build e dependências |
| `ci` | Pipelines de CI/CD |
| `chore` | Tarefas diversas que não afetam src/test |

**Formato:** `<tipo>(<escopo>): <resumo>`

**Exemplos:**
```
feat(readme): inclusão do campo about me
fix(api): tratar null pointer ao criar pedido
docs(contrib): adicionar guia de pull request
```

---

## Convenções de Nomenclatura de Branches

| Padrão | Exemplo |
| ------ | ------- |
| `feature/<id>-<descricao>` | `feature/1234-criar-endpoint-pedidos` |
| `fix/<id>-<descricao>` | `fix/235-bug-null-pointer-checkout` |
| `chore/<descricao>` | `chore/atualizar-dependencias` |
| `hotfix/<descricao>` | `hotfix/corrigir-regra-frete` |
| `docs/<descricao>` | `docs/roteiro-git-pr` |

---

## Git Stash — Quando usar?

O `git stash` é útil quando você precisa trocar de branch no meio do desenvolvimento ou atualizar a `main` sem perder o que já começou. Ele guarda as mudanças temporariamente e permite recuperá-las depois.

**Fluxo típico:**
```bash
# Guardando trabalho em andamento
git stash save "ajustes parciais no header"

# Trocando de branch
git checkout main
git pull

# Voltando para a feature e recuperando
git checkout feature/minha-feature
git stash pop
```
