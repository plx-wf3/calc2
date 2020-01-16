# Configuration de git 

# Utiliser un editeur par defaut 
```shell script
   git config --global -e
   git config --global core.editor vim 
   git config --global -e
```


 ## Ajouter l'outil Perforce P4Merge
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

