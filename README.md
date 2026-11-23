# General Task Loop

Два скилла для задач в Claude Code и Codex.

- [`my-task-loop`](skills/my-task-loop/SKILL.md) проводит по согласуемым этапам от разбора и постановки до приёмки. Внешний [Spec Kit](https://github.com/github/spec-kit) готовит полную спеку в репозитории задачи до `tasks.md` включительно.
- [`sam-reshu`](skills/sam-reshu/SKILL.md) согласует границы в начале и дальше ведёт задачу самостоятельно до проверенного результата или PR/MR.

[Шаблон постановки](skills/my-task-loop/references/postanovka-template.md)

## Установка

```sh
git clone https://github.com/Winkey86/general-task-loop.git
cd general-task-loop

skills_dir="$HOME/.agents/skills"  # Codex
# skills_dir="$HOME/.claude/skills"  # Claude Code
mkdir -p "$skills_dir"
ln -s "$PWD/skills/my-task-loop" "$PWD/skills/sam-reshu" "$skills_dir/"
```

Для Claude Code используй вторую строку `skills_dir`. Для установки в оба клиента повтори `mkdir` и `ln` с другим путём. Если скилл с таким именем уже установлен, проверь существующую версию перед заменой.

## Запуск

Открой новую сессию в репозитории задачи. После ключа передай описание, путь к файлу или ссылку на issue.

| Claude Code | Codex |
| --- | --- |
| `/my-task-loop fix-login Исправить возврат после входа` | `$my-task-loop fix-login Исправить возврат после входа` |
| `/sam-reshu fix-login Исправить возврат после входа` | `$sam-reshu fix-login Исправить возврат после входа` |

Чтобы продолжить в другой сессии, вызови тот же скилл с тем же ключом. При смене машины или checkout передай ветку, файл состояния и указанные в нём документы. [Как передать задачу](skills/my-task-loop/references/workflow.md#передача-работы)
