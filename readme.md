## Fonctionnalités

- Afficher un portail d'équipe avec des rubriques (onglets)
- Chaque rubrique correspond à un dossier spécifique côté serveur
- Dans chacun de ces dossiers on trouve un bundle js d'un widget qui sera référencé dans la page affichée selon l'onglet demandée.
- Ce bundle peut-être :
    - un composant écrit en React
    - un simple bout de code écrit en vanilla JS qui se charge de créer une iFrame pour charger une application web existante dans le portail
- Ce bundle doit être autonome et peut communiquer avec n'importe quelle service REST du réseau, pourvu que les entêtes CORS soit gérés dans ledit service et dans ledit bundle.

### Ergonomie / Design du portail

Basique, ce portail se compose d'une seule page servie pour différentes routes correspondants aux différents onglets du portail, eux-mêmes calculés en fonction des sous dossiers présents dans le dossier d'application `sections`.

Ainsi, si l'application se présente comme suit :

```
/dist
    /sections
        /calendar
            bundle.js
        /reports
            bundle.js
        /business-translator
            bundle.js
```

Alors :
- la page html servie comportera les 3 onglets :
    - `Calendar`
    - `Reports`
    - `Business translator`
- l'application acceptera des requêtes sur les routes
    - `/calendar`
    - `/reports`
    - `/business-translator` 

Par défaut, le nom de l'onglet sera celui du dossier avec une majuscule au début.
Si le nom du dossier contient des `-`, ceux-ci seront remplacés par des espaces pour générer le titre de l'onglet.

Concernant la mise en forme, l'application utilise bootstrap.

Chaque composant JS doit porter ses propres styles si nécessaire ou à défaut utiliser la structure et les classes bootstrap.

