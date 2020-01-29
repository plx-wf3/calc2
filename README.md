# Configuration de git 

## definir votre nom et votre adresse mail 
```shell script
   git config --global user.name "Herve"
   git config --global user.email dockerlite@gmail.com
```

## Pour vous aider, definir des aliases suivants
``` git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.ci commit
    git config --global alias.st status
    git config --global alias.last 'log -1 HEAD'
```
### aliases plus complexes a copier/coller dans le fichier .gitconfig
```shell script
    lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen--> %cr%Creset by %Cblue%cN <%cE>%Creset' --abbre
    v-commit --date=relative
    hist = log --pretty=format:\"%h %ad | %s%d [%an]\" --graph --date=short
```
### Alias avec une fonction ecrite dans une commande shell
 ```shell script
     git config --local alias.dumpvalues "! f() { echo 'copying config' \$1; git config --list --\$1 > \$2; }; f"
```

# Utiliser un editeur par defaut 
```shell script
   git config --global -e
   git config --global core.editor vim 
   git config --global -e
```

## Outils difftools 
### Ajouter l'outil Perforce P4Merge
 ```shell script
  mkdir p4v
  cd p4v
  wget http://filehost.perforce.com/perforce/r19.2/bin.linux26x86_64/p4v.tgz
  tar -zxvf p4v.tgz
  sudo cp -r p4v-2019.2.1904275/ /opt
  sudo ln -s /opt/p4v-2019.2.1904275/bin/p4merge /usr/local/bin/p4merge
  vi ~/.gitconfig                
```
et 
ajouter a la fin de ce fichier .gitconfig le code suivant:
```shell script
[diff]
   tool = p4merge
[difftool]
   prompt = false
[difftool "p4merge"]
   cmd = p4merge "$LOCAL" "$REMOTE"
   keepTemporaries = false
   trustExitCode = false
   keepBackup = false
```
## Ajouter la completion pour entrer plus facilement les commandes
```shell script
   curl https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash
   vi ~/.bash_profile
      # ajouter le code suivant 
         if [ -f ~/.git-completion.bash ]; then
             . ~/.git-completion.bash
         fi
   chmod +x ~/.git-completion.bash
   source ~/.bash_profile
```


