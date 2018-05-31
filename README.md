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

# lancement de votre super application

avec le terminal, placez-vous dans le répertoire de votre application, puis lancez-le avec la commande:
```
meteor
```

(oui, c'est aussi simple que ça!)

# conseils

1. lorsque vous lancez la commande
```
meteor create maSuperAppli
```
évitez les noms comportant des espaces ou des tirets, vraiment! le npm contenu dans Meteor semble ne vraiment pas aimer ça. Faites-moi confiance, ça vous évitera de perdre beaucoup de temps. et au passage, Meteor a sa propre version de npm et ne nécessite pas d'avoir au préalable une installation globale de npm sur sa machine.

2. erreur avec la commande ```meteor``` version 1.6.1_1 sur windows

il se peut que lorsque vous lancez la commande ```meteor```, meteor vous insulte copieusement et qu'une erreur apparaisse:

```console
Error: The @babel/runtime npm package could not be found in your node_modules directory. Please run the following command to install it:
meteor npm install --save @babel/runtime
```
vous décidez alors de lancer cette commande suggérée par météor, et là un nouveau message d'erreur apparaît:

```console
'npm' is not a Meteor command. See 'meteor --help'.
```

La seule solution que j'ai trouvé pour l'instant est d'utiliser une installation globale de npm et d'utiliser la commande:

```console
npm install --save @babel/runtime
```

Maintenant, vous pouvez à nouveau lancer la commande

```console
meteor
```
et tout devrait fonctionner, vous verrez s'afficher

```console
[[[[[ ~\E\meteor\votreSuperAppli ]]]]]

=> Started proxy.
=> Started MongoDB.
=> Started your app.

=> App running at: http://localhost:3000/
   Type Control-C twice to stop.
```

rendez-vous dans votre navigateur à l'adresse:
```
localhost:3000
```

et vous verrez s'afficher l'application de démo de Meteor

![screenshot01](https://github.com/adriengodoy/meteor/blob/master/img/meteor_demo_app_screenshot.png "screenshot")


# structure d'un projet Meteor

Si vous ouvrez votre projet dans votre éditeur préféré, vous pourrez vous appercevoir qu'un projet Meteor contient les éléments suivants:

    ˫ ▸ 📁 .meteor/
    ˫ ▾ 📁 client/
		 ˪  /* main.css
		 ˪  <> main.css
		 ˪  /* main.js
    ˫ ▾ 📁 node_modules/
		 ˪ ▸ 📁 @babel/
		 ˪ ▸ 📁 core-js/
		 ˪ ▸ 📁 regenerator-runtime/
    ˫ ▾ 📁 server/
		 ˪ /* main.js
    ˪ 📄 .gitignore
    ˪ /* package-lock.json
    ˪ /* package.json