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

## Uso recomendado

1. Edite arquivos.
2. Use `git status` para revisar o que mudou.
3. Adicione as mudanças com `git add`.
4. Faça o commit com `git commit -m "tipo: descrição"`.
5. Envie para o GitHub com `git push`.
