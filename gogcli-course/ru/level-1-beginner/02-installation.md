---
title: "Установка gogcli"
weight: 2
bookToc: true
---

# Установка gogcli

## Выберите способ установки

### Вариант 1: Homebrew (macOS и Linux)

```bash
brew install steipete/tap/gogcli
```

Проверьте установку:

```bash
gog --version
```

### Вариант 2: Arch Linux (AUR)

```bash
yay -S gogcli
```

### Вариант 3: Сборка из исходного кода

Подходит для любой системы с установленным Go:

```bash
git clone https://github.com/steipete/gogcli.git
cd gogcli
make
```

Бинарный файл появится в `./bin/gog`. Переместите его в PATH:

```bash
sudo cp ./bin/gog /usr/local/bin/
```

## Проверка установки

```bash
gog --help
```

Вы должны увидеть список доступных команд: `gmail`, `calendar`, `drive` и другие.

## Получение справки

```bash
# Общая справка
gog --help

# Справка по сервису
gog gmail --help

# Справка по конкретной команде
gog gmail search --help

# Полный список команд
GOG_HELP=full gog --help
```

## Автодополнение в терминале (необязательно)

**Bash:**
```bash
source <(gog completion bash)
```

**Zsh:**
```zsh
echo 'eval "$(gog completion zsh)"' >> ~/.zshrc
```

**Fish:**
```fish
gog completion fish > ~/.config/fish/completions/gog.fish
```

## Далее

В следующем уроке вы настроите аутентификацию для доступа к вашему аккаунту Google.
