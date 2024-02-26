Avant de commencer, ce projet avait uniquement pour objectif de découvrir le domaine de la cybersécurité et s'amusé à contourner les différents antivirus.
Je ne partagerais donc pas le code de ce projet. Je n'encourage évidemment pas l'utilisation de ce genre de programme.

## Présentation

Le virus que j'ai créé est un virus polymorphique utilisant la stéganographie pour se cacher dans une image. Je parle de virus mais c'est en réalité un compilateur de payload.
Le compilateur marche en deux étapes, la première est de coder son payload en python, puis on compile le fichier payload pour qu'il tienne dans une image. Le compilateur crée également un fichier executable qui va extraire le payload de l'image et l'exécuter.
Alors à quoi ça sert de mettre le payload dans une image si on doit cliquer sur un fichier executable pour l'exécuter ? Et bien c'est là que la stéganographie entre en jeu. Le fichier executable va extraire le payload de l'image et l'exécuter sans que l'utilisateur ne s'en rende compte.
L'anti-virus ne va pas détecter le payload car il est caché dans l'image et il ne va pas détecter le fichier executable car il n'est pas connu. De plus, le payload est compilé à chaque fois, ce qui fait que sa signature change à chaque fois.

## Polymorphisme

Pour comprendre le polymorphisme, il faut d'abord comprendre le fonctionnement d'un anti-virus. Il existe plusieurs méthodes pour détecter un virus, mais la plus utilisé est la comparaison de la signature du fichier avec une base de données de signatures de virus connue. Si la signature du fichier est identique à celle d'un virus connu, alors l'antivirus va bloquer le fichier.
Pour contourner cette détection, la méthode la plus simple est de modifier le code du virus pour que sa signature soit différente de celle du virus connu.
Ce type de virus est appelé virus polymorphique. Dans mon cas, la signature est différente à chaque compilation.

## Stéganographie

La stéganographie en informatique est le fait de cacher des données dans un fichier. Dans mon cas, je cache le payload dans une image.
Pour cela, j'utilise la librairie PIL (Python Imaging Library) qui permet de manipuler des images en python.
Le principe est simple, je récupère les pixels de l'image et je modifie les bits de poids faible de chaque pixel pour y mettre les bits du payload. Les bits de poids faible sont les bits les moins significatifs d'un nombre. Par exemple, pour le nombre 5, les bits de poids faible sont 1 et 0. Les bits de poids fort sont les bits les plus significatifs d'un nombre. Pour le nombre 5, les bits de poids fort sont 0 et 0.
Pour extraire le payload de l'image, je récupère les bits de poids faible des pixels de l'image et je les concatène pour obtenir le payload.

Avant de cacher le payload dans l'image, je l'obfusque afin de rendre son analyse plus difficile. Le code est également encrypté avec une clé AES et encodé en base64.

## Compilation

Pour compiler le payload, j'utilise la librairie pyinstaller qui permet de compiler un fichier python en executable.
L'exécutable comprend la clé AES afin de décrypter le payload et pouvoir l'exécuter.

## Résultat

Voici le résultat de l'analyse du fichier executable par VirusTotal :
- Photo comprenant le payload : 0/56
- Fichier executable : 2/56

Le score n'est pas parfait mais il est très bon pour un petit projet comme celui-ci. De plus, les seuls antivirus qui détectent le fichier executable sont des antivirus très peu connus.
Les gros antivirus comme Avast, Kaspersky, McAfee, Norton, Windows Defender, etc... ne détectent pas le fichier executable.
Après avoir tester avec un token grabber en python, le fichier executable n'est pas détecté par les antivirus. Il est donc possible de créer un virus qui vole des informations sans être détecté par les antivirus même en 2023.