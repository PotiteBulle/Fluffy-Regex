# Fluffy-Regex
### Voici des exemples de regex de sécurité de niveau avancé que vous pouvez mettre en place avec le système Automod dans vos serveurs Discord afin de protéger vos utilisateur·rices au mieux.


- **Liens avec des redirections suspectes**:

``` \b(?:http|https):\/\/(?:www\.)?[\w\-]+\.(?:com|net|org)\/\S*?[?&](?:redirect|url|r)= ```

**Explication** : *Cette regex capture les liens qui utilisent des paramètres de redirection comme "redirect", "url", ou "r". Les redirections peuvent masquer la destination réelle d'un lien.*


- **Liens avec des paramètres de requête suspects**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/?\S*\?(?:.*?)(?:tracking|ref|utm|session)= ```

**Explication** : *Cette regex identifie les liens contenant des paramètres de requête tels que "**tracking**", "**ref**", "**utm**", ou "**session**", qui peuvent indiquer des tentatives de suivi ou de collecte de données.*


- **Liens avec des extensions de fichier suspectes**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/.*?\.(exe|zip|rar|js|vbs|bat) ```

**Explication** : *Cette regex cible les liens pointant vers des fichiers exécutables ou compressés, qui peuvent contenir des logiciels malveillants.*


- **Liens avec des caractères spéciaux (phishing)**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/\S*[^\w\s\/][\S]* ```

**Explication** : *Cette regex attrape les liens avec des caractères spéciaux inhabituels dans l'URL, ce qui pourrait indiquer une tentative de masquer des intentions malveillantes.*


- **Liens avec des chaînes encodées en base64 (pishing)**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/\S*?[A-Za-z0-9+/=]{8,} ```

**Explication** : *Cette regex détecte les liens contenant des chaînes de caractères encodées en base64, qui sont parfois utilisées pour obfusquer des informations ou des scripts malveillants.*


- **Liens avec des paramètres de session (link token grab)**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/\S*?[?&](?:session|token|auth)= ```

**Explication** : *Cette regex capture les liens qui incluent des paramètres tels que "session", "token", ou "auth", qui peuvent être utilisés pour des sessions d'utilisateur ou des authentifications malveillantes.*


- **Liens avec des requêtes GET suspectes (link token grab)**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/\S*\?(?:\S*?[&?](?:id|key|token|password|secret)=) ```

**Explication** : *Cette regex détecte les liens contenant des paramètres GET comme "id", "key", "token", "password", ou "secret", qui peuvent exposer des informations sensibles.*


- **Liens avec des URL générées dynamiquement**:

``` \b(?:http|https):\/\/[\w\-]+\.(?:com|net|org)\/\S*?[0-9]{3,}\/\S* ```

**Explication** : *Cette regex identifie les liens avec des segments numériques significatifs dans l'URL, ce qui peut indiquer des URL générées dynamiquement pour des campagnes de phishing.*


- **Liens avec des noms de domaine générés automatiquement**:

``` \b(?:http|https):\/\/[\w\-]{10,}\.(?:com|net|org)\/\S* ```

**Explication** : *Cette regex détecte les domaines avec des noms générés automatiquement ou aléatoires, souvent utilisés pour des activités malveillantes.*


- **Liens avec des sous-domaines inhabituels**:

``` \b(?:http|https):\/\/(?:[\w\-]{3,}\.){2,}[\w\-]+\.(?:com|net|org)\/\S* ```

**Explication** : *Cette regex attrape les liens avec des sous-domaines inhabituels ou multiples, ce qui peut être un indicateur de manipulation ou de phishing.*


- **Liens avec des séquences aléatoires**:

``` \b(?:http|https):\/\/[\w\-]{10,}\.(?:com|net|org)\/\S*?[a-zA-Z0-9]{10,} ```

**Explication** : *Cette regex détecte les liens contenant des séquences aléatoires dans l'URL, souvent utilisées pour masquer des activités malveillantes ou pour générer des pages temporairement dans un usage malveillant.*


- **Détection de mots déguisés par des caractères spéciaux ou des chiffres (Leet Speak)**:

``` \b([fF][uU][cC][kK]|[sS][hH][i1lL][tT]|[bB][i1lL][tT][cC][hH])\b```

**Explication**: *Cette regex détecte les versions leet speak courantes de termes offensants où les lettres sont remplacées par des caractères visuellement similaires.*


- **Détection d'injections de scripts (XSS Simple)**:

``` (<\s*script.*?>.*?</\s*script\s*>|<\s*img\s+src\s*=\s*['\"]?javascript:.*?>)```

**Explication**: *Cette expression permet de détecter des injections XSS basiques via des balises
**script** ou des images avec un attribut **src** de type JavaScript.*


- **Filtrage de textes obscurcis par des caractères similaires (comme O vs 0, I vs l)**:

``` \b([o0]{1,2}[b8]{1,2}[s5]{1,2}c[3e]{1,2}[n9]{1,2})\b```

**Explication**: *Cette regex cible les mots obscurcis en combinant des caractères similaires, souvent utilisés pour contourner la modération (par exemple, remplacer des lettres par des chiffres).*
