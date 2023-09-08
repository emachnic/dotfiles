# Dotfiles Configuration

## Install Onto a New System

1. `alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'`
2. `echo ".cfg" >> .gitignore`
3. `git clone --bare <git-repo-url> $HOME/.cfg`
4. `alias config='/usr/bin/git --git-dir=$HOME/.cfg/ --work-tree=$HOME'`
5. `config checkout`
6. `config config --local status.showUntrackedFiles no`

## Backup Existing Config

```bash
mkdir -p .config-backup && \
config checkout 2>&1 | egrep "\s+\." | awk {'print $1'} | \
xargs -I{} mv {} .config-backup/{}
```
