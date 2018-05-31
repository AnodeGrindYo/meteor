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
		 ˪  <> main.html
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


* le dossier .meteor/ contient les fichiers de configuration du projet.
* le dossier client/ est le point d'entrée du code frontend (qui sera exécuté côté client).
* le dossier node_modules contient les modules nodejs installés.
* le dossier server/ est le point d'entrée du code backend (exécuté côté serveur).
* package-lock.json est généré automatiquement pour toutes les opérations où npm modifie l'arborescence node_modules ou package.json. Il décrit l'arborescence exacte qui a été générée, de sorte que les installations ultérieures peuvent générer des arborescences identiques, indépendamment des mises à jour de dépendances intermédiaires.
* package.json contient diverses métadonnées relatives projet. Ce fichier est utilisé pour donner des informations à npm qui lui permettent d'identifier le projet ainsi que de gérer les dépendances du projet. Il peut également contenir d'autres métadonnées telles qu'une description de projet, la version du projet dans une distribution particulière, des informations de licence, voire des données de configuration, utiles à la fois pour npm et pour les utilisateurs finaux du package.


# les commandes Meteor

## meteor help
```meteor help``` affiche de l'aide sur l'utilisation de meteor en ligne de commande. Vous pouvez aussi utiliser ```meteor help nom_de_la_commande``` pour obtenir de l'aide sur une commande spécifique.

## meteor run
démarre un serveur de développement Meteor dans le projet courrant. Chaque fois que vous enregistrez une modification dans le code du projet, celle-ci est immédiatement détectée et appliquée à l'application en cours. Vous pouvez simplement utiliser la commande ```meteor``` qui produit le même résultat que ```meteor run```

vous pouvez également passer des options à Node.JS. Pour celà, utilisez la variable d'environnement ```NODE_OPTION```. Par exemple ````NODE_OPTION='--debug' ``` ou ```NODE_OPTION='--debug-brk'```

Vous pouvez également spécifier un port à écouter différent du port par défaut (le port 3000). Pour modifier le port par défaut, utilisez ```--port [PORT]``` (le serveur de développement utilise aussi le port ````N+1```) pour l'instance MongoDB par défaut.

Par exemple ```meteor run --port 4000``` va démarrer le serveur ed développement sur ```http://localhost:4000``` et MongoDB sur ```mongodb://localhost:4001```

vous pouvez obtenir la liste complète des options avec ```meteor help run```


## meteor debug

lance le projet, mais suspend le process serveur à des fins de débogage. Le processus du serveur sera suspendu juste avant la première déclaration du code du serveur qui devrait s'exécuter normalement. Pour continuer l'exécution du code du serveur, utilisez Node Inspector ou le débogueur de ligne de commande (d'autres instructions seront imprimées dans la console).

des breakpoints peuvent être ajoutés en utilisant le mot-clé ```debugger```, ou à travers l'UI web de Node Inspector (onglet "Sources")

le débogueur de process serveur va écouter les connections entrantes du client de débogage (Node Inspector, par exemple), par défaut sur le port 5858. Pour utiliser un port différent, utilisez l'option ```--debug-port [PORT]```

la même fonctionnalité de débogage peut être obtenue en ajoutant l'option ```--debug-port [PORT]``` à d'autres commandes meteor, comme par exemple ```meteor run``` ou ```meteor test-package```

**note:** il y a actuellement un bug dans ```node-inspector```: appuyer sur la touche "entrée" après une commande dans la console Node Inspector ne va pas envoyer la commande au serveur. Comme alternative, vous pouvez utiliser safari ou ```meteor shell``` jusqu'à ce que le bug soit résolu


## meteor create nomDuProjet

crée un projet Meteor. Par défaut, crée un dossier nomDuProjet et copie dedans l'application de démo Meteor. Vous pouvez utiliser un chemin relatif ou absolu.

### flags

```--bare```
crée un projet vide.

```--full```
crée un projet plus complet dont la structure correspond à celle recommandée par le [guide Meteor](https://guide.meteor.com/)

```--package```
crée un nouveau package. Si cette commande est utilisée dans un projet existant, un nouveau package sera ajouté dans le dossier des packages

### packages

<table><thead><tr><th></th><th>Default</th><th>`--bare`</th><th>`--full`</th></tr></thead><tbody><tr><td>[autopublish](https://atmospherejs.com/meteor/autopublish)</td><td>X</td><td></td><td></td></tr><tr><td>[blaze-html-templates](https://atmospherejs.com/meteor/blaze-html-templates)</td><td>X</td><td></td><td>X</td></tr><tr><td>[ecmascript](https://atmospherejs.com/meteor/ecmascript)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[es5-shim](https://atmospherejs.com/meteor/es5-shim)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[insecure](https://atmospherejs.com/meteor/insecure)</td><td>X</td><td></td><td></td></tr><tr><td>[johanbrook:publication-collector](https://atmospherejs.com/meteor/johanbrook:publication-collector)</td><td></td><td></td><td>X</td></tr><tr><td>[kadira:blaze-layout](https://atmospherejs.com/meteor/kadira:blaze-layout)</td><td></td><td></td><td>X</td></tr><tr><td>[kadira:flow-router](https://atmospherejs.com/meteor/kadira:flow-router)</td><td></td><td></td><td>X</td></tr><tr><td>[less](https://atmospherejs.com/meteor/less)</td><td></td><td></td><td>X</td></tr><tr><td>[meteor-base](https://atmospherejs.com/meteor/meteor-base)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[mobile-experience](https://atmospherejs.com/meteor/mobile-experience)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[mongo](https://atmospherejs.com/meteor/mongo)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[practicalmeteor:mocha](https://atmospherejs.com/meteor/practicalmeteor:mocha)</td><td></td><td></td><td>X</td></tr><tr><td>[reactive-var](https://atmospherejs.com/meteor/reactive-var)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[shell-server](https://atmospherejs.com/meteor/shell-server)</td><td>X</td><td>X</td><td></td></tr><tr><td>[standard-minifier-css](https://atmospherejs.com/meteor/standard-minifier-css)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[standard-minifier-js](https://atmospherejs.com/meteor/standard-minifier-js)</td><td>X</td><td>X</td><td>X</td></tr><tr><td>[static-html](https://atmospherejs.com/meteor/static-html)</td><td></td><td>X</td><td></td></tr><tr><td>[tracker](https://atmospherejs.com/meteor/tracker)</td><td>X</td><td>X</td><td>X</td></tr></tbody></table>


## meteor login/logout

se connecte/se déconnecte de votre compte en utilisant le système d'autentification de Meteor.

vous pouvez passer ```METEOR_SESSION_FILE=token.json``` avant ```meteor login``` pour générer un jeton de session de connexion afin que vous n'ayez pas à partager vos informations de connexion avec des fournisseurs de services tiers.

une fois que vous avez votre compte, vous pouvez vous y connecter/déconnecter en ligne de commande. Vous pouvez également vérifier votre nom d'utilisateur avec ```meteor whoami```


## meteor deploy **site**

Déploie le projet situé dans le répertoire courrant vers [Galaxy](https://www.meteor.com/hosting), qui est une plateforme **as-a-service** crée spécialement pour héberger les applications Meteor. Mais rien ne vous empêche de déployer votre application sur une autre plateforme, comme [Heroku](https://medium.com/@leonardykris/how-to-run-a-meteor-js-application-on-heroku-in-10-steps-7aceb12de234)

... To be continued ...