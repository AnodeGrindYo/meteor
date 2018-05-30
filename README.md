# installation de meteor


## windows

1. installez d'abord chocolatey: [site officiel chocolatey](https://chocolatey.org/install)
ou ouvrez un powershell en admin et entrez la commande suivante:
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

puis testez votre installation dans un terminal avec la commande ```choco```

2. installez meteor: [site officiel meteor](https://www.meteor.com/install)
ou entrez la commande suivante dans un terminal: 
```choco install meteor```


## linux/OSX

lancez la commande suivante dans votre terminal: ```curl https://install.meteor.com/ | sh```


# creation d'un projet meteor

dans le terminal, nom_projet étant le nom de votre projet, entrez la commande:
```
meteor create nom_projet
```

