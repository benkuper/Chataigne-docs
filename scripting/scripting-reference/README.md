# Référence de scripting

Vous trouverez ici une référence quasi exhaustive sur les fonctions spécifiques de Chataigne.

{% hint style="success" %}
Les scripts en Chataigne sont basés sur une version simplifiée de Javascript. La plupart des fonctions sont disponibles, mais certaines peuvent manquer. Si certaines fonctions vous manquent, veuillez me contacter et envisager de faire un don (https://github.com/sponsors/benkuper) pour que je puisse passer plus de temps à améliorer Chataigne !
{% endhint %}

## Fonctions communes

Il y a peu de fonctions communes que vous pouvez utiliser, quel que soit le type de script.

{% hint style="info" %}
Aucune des fonctions ci-dessous n'est nécessaire lors de la réalisation d'un script, ce sont juste des fonctions d'aide.  
Si vous n'en avez pas besoin, ne les ajoutez pas à votre script, car Chataigne optimisera votre script en fonction des fonctions disponibles dans celui-ci.
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>init()</b>
      </td>
      <td style="text-align:left">Si elle est présente, cette fonction sera appelée juste après le chargement du script.</td>
      <td
      style="text-align:left">
        <p><code>fonction init() {</code>
        </p>
        <p><code>//init vos valeurs, enregistrez les choses et attribuez des variables</code>
        </p>
        <p><code>}</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>update(</b><em>deltaTime</em><b>)</b>
      </td>
      <td style="text-align:left">Si elle est présente, cette fonction sera appelée régulièrement au rythme spécifié par
        le &quot;Taux de mise à jour&quot ; paramètre de script. Ce paramètre n'est visible que
        lorsque la fonction est présente dans le scénario. Vous pouvez également modifier le taux
        à partir du script en appelant <b>script.setUpdateRate</b><em>(rate).</em> voir
        ci-dessous pour plus d'informations.</td>
      <td style="text-align:left">
        <p><code>fonction update(deltaTime)</code>
        </p>
        <p><code>{</code>
        </p>
        <p> <code>script.log(&quot;Delta time : &quot ; + deltaTime);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </corps>
</table>### Paramètres et déclencheurs

Tous les paramètres et déclencheurs ont des méthodes communes et des méthodes spécifiques 

#### Méthodes et propriétés communes

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>getParent()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce paramètre</td>
      <td style="text-align:left"><code>myParam.getParent();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Définit les paramètres name</td>
      <td style="text-align:left"><code>myParam.setName(&quot;new name&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Définit un paramètre&apos;s attribut.</p>
        <p>Tous les paramètres obtiennent :
          <br /><em><b>readonly : </b></em> définit le paramètre comme non modifiable</p>
        <p><em><b>description : </b></em>modifier la description de l'infobulle</p>
        <p><em><b>activé : </b></em>activer ou désactiver ce paramètre</p>
        <p><em><b>alwaysNotify : </b></em>set the alwaysNotify flag (if true, this
          déclenchera des mises à jour même si la valeur fixée est la même qu'auparavant).
          <br />Plus d'informations pour des paramètres spécifiques dans chaque section de paramètres&apos;s. </p>
      </td>
      <td style="text-align:left">
        <p><code>myParam.setAttribute(&quot;readonly&quot ;,true);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;description&quot ;,&quot ; new description&quot ;);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;enabled&quot ;,false);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;alwaysNotify&quot ;, true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>isParameter()</b>
      </td>
      <td style="text-align:left">retourne si la cible est un paramètre ou un déclencheur</td>
      <td style="text-align:left"><code>var isParam = myTarget.isParameter();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">Il s'agit de l'identificateur de nom de l'objet, comme vous le feriez dans un
        script.</td>
      <td style="text-align:left"><code>script.log(myParam.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">C'est le &quot;joli nom&quot ; de l'objet, tel que vous le voyez dans le
        Inspecteur.</td>
      <td style="text-align:left"><code>script.log(myParam.niceName);</code>
      </td>
    </tr>
  </corps>
</table>######## Déclencheur

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **trigger\(\)** | Retourne la valeur de ce paramètre | `myTrigger.trigger();` |

#### Paramètre de flottabilité

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce paramètre</td>
      <td style="text-align:left"><code>var value = myFloatParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la valeur de ce paramètre</td>
      <td style="text-align:left"><code>myFloatParam.set(.5);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs spécifiques :</p>
        <p><em><b>ui : </b></em> L'interface utilisateur à utiliser pour afficher ce paramètre. Valeurs acceptées
          sont : <em><b>time, slider, stepper, label</b></em>
        </p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;ui&quot ;, &quot;time&quot ;);</code>
      </td>
    </tr>
  </corps>
</table>#### Paramètre entier

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce paramètre</td>
      <td style="text-align:left"><code>var value = myIntParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la valeur de ce paramètre</td>
      <td style="text-align:left"><code>myIntParam.set(2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs spécifiques :</p>
        <p><em><b>hexMode : </b></em>Afficher la valeur en décimal ou en hexadécimal.</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;hexMode&quot ;, true);</code>
      </td>
    </tr>
  </corps>
</table>#### Paramètre booléen

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **get\(\)** | Retourne la valeur de ce paramètre | `var value = myBoolParam.get();` |
| **set\(**_value_**\)** | Définit la valeur de ce paramètre | `myBoolParam.set(true);` |

#### Paramètre de la chaîne

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce paramètre</td>
      <td style="text-align:left"><code>var value = myStringParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la valeur de ce paramètre</td>
      <td style="text-align:left"><code>myStringParam.set(&quot;super&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs spécifiques :</p>
        <p><em><b>multiline</b></em> : si le paramètre peut être multiligne</p>
        <p><em><b>préfixe</b></em> : ajouter un préfixe avant la valeur</p>
        <p><em><b>suffixe</b></em> : ajouter un suffixe après la valeur</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;multiline&quot ;, true);</code>
      </td>
    </tr>
  </corps>
</table>#### Paramètre de couleur

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce paramètre. Le résultat est un tableau contenant
        [r,g,b,a], les valeurs sont comprises entre 0 et 1</td>
      <td style="text-align:left">
        <p><code>var value = myColorParam.get();</code>
        </p>
        <p><code>script.log(&quot;green : &quot;+value[1]);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la valeur de ce paramètre. Vous pouvez soit définir la valeur avec ARGB
        valeur hex, [r,g,b,a] tableau flottant, ou r,g,b,a valeurs séparées. r, g et
        Les valeurs b sont toujours comprises entre 0 et 1 et l'alpha est facultatif (vous pouvez spécifier
        r,g,b seulement);</td>
      <td style="text-align:left">
        <p><code>//ceci est réglé sur cyan alpha 100%</code>
        </p>
        <p><code>myColorParam.set(0xff00ffffff);</code>
        </p>
        <p><code>myColorParam.set([0,1,1,1]);</code>
        </p>
        <p><code>myColorParam.set(0,1,1,1);</code>
        </p>
      </td>
    </tr>
  </corps>
</table>#### Paramètre cible

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de la chaîne de l'adresse cible</td>
      <td style="text-align:left"><code>var address = myTargetParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getTarget()</b>
      </td>
      <td style="text-align:left">Retourne la cible réelle sélectionnée</td>
      <td style="text-align:left"><code>var target = myTargetParam.getTarget();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la valeur de la chaîne de caractères de l'adresse de target&apos;s.</td>
      <td style="text-align:left"><code>myTargetParam.set (&quot;/root/modules/osc&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs spécifiques :</p>
        <p><em><b>root </b></em> : le conteneur racine à partir duquel la recherche doit être effectuée</p>
        <p><em><b>searchLevel </b></em> : préciser le niveau maximum à rechercher dans le
          root</p>
        <p><em><b>showParameters </b></em> : si la cible est contrôlable, cacher ou montrer
          paramètres</p>
        <p><em><b>showTriggers </b></em> : si la cible est contrôlable, cacher ou montrer
          déclencheurs</p>
        <p><em><b>labelLevel </b></em> : le niveau des parents à afficher dans l'IU.</p>
      </td>
      <td style="text-align:left">
        <p><code>myTargetParam.setAttribute (&quot;searchLevel&quot ;,2);</code>
        </p>
        <p><code>myTargetParam.setAttribute (&quot;root&quot ;, root.sequences);</code>
        </p>
      </td>
    </tr>
  </corps>
</table>#### Paramètre Enum

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **addOption\(**_label, value_**\)** | Ajouter une option à la liste | `myEnumParam.addOption("nouvelle option",3);` |
| **get\(\)** | Obtenez le label sélectionné | `var label = myEnumParam.get();` |
| **getData\(\)** | Obtenir les données sélectionnées | `var data = myEnumParam.getData();` |
| **set\(**_label_**\)** | Définit la valeur avec l'étiquette fournie | `myEnumParam.set("nouvelle option");` |
| **removeOptions\(\)** | Supprime toutes les options. | `myEnumParam.removeOptions();` |

#### Paramètre de fichier

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>setAttribut(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">Définissez un attribut FileParameter spécifique (voir exemples)</td>
      <td style="text-align:left"><code>myFileParam.setAttribute (&quot;directoryMode&quot ;,true);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Consultez le contenu du fichier. Si <em><b>asJSON </b></em>est <em>vrai, </em>alors
        le contenu sera analysé et renvoyé sous la forme d'un Object.</td>
      <td style="text-align:left">
        <p><code>var myTextContent = myFileParam.readFile ();</code>
        </p>
        <p><code>var myJSONContent = myFileParam.readFile (true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(data, </b><em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Ecrivez le contenu ou une chaîne d'un Objet dans le fichier sélectionné. Si le
        existe, <em><b>overwriteIfExists </b></em> vous permettra de décider si
        pour l'écraser ou non (false par défaut).</td>
      <td style="text-align:left">
        <p><code>données variables = &quot;super&quot;;</code>
        </p>
        <p><code>myFileParam.writeFile (données, vrai);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getAbsolutePath()</b>
      </td>
      <td style="text-align:left">Retourne le chemin absolu de ce fichier.</td>
      <td style="text-align:left"><code>var path = myFileParam.getAbsolutePath();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>launchFile(</b><em>arguments<b>)</b></em>
      </td>
      <td style="text-align:left">Ceci lancera le fichier sélectionné avec les <em><b>arguments</b> </em>fournis</td>
      <td
      style="text-align:left"><code>myFileParam.launchFile<br />(&quot;--verbose&quot ;)</code>
        </td>
    </tr>
  </corps>
</table>#### Paramètre Point2D

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **get\(\)** | Retourne la valeur de ce paramètre | `var value = myP2DParam.get();` |
| **set\(**_x, y_**\)** | Définit la valeur de ce paramètre | `myP2DParam.set(.5, 2);` |

#### Paramètre Point3D

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **get\(\)** | Retourne la valeur de ce paramètre | `var value = myP3DParam.get();` |
| **set\(**_x, y, z_**\)** | Définit la valeur de ce paramètre | `myP3DParam.set(.5, 2, -1);` |

### Conteneur

Les conteneurs sont tout objet qui contient des paramètres ou d'autres récipients. Si vous visez quelque chose de la hiérarchie (_root.\*_ **** ou _local.\*_\), ce sera soit un conteneur d'un paramètre, donc si ce n'est pas un paramètre, alors c'est un conteneur.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>getChild(</b><em>childName</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne le paramètre ou le conteneur avec le nom fourni.</td>
      <td style="text-align:left"><code>var child = myContainer.getChild(&quot;activity&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getParent()</b>
      </td>
      <td style="text-align:left">Retourne le conteneur parent</td>
      <td style="text-align:left"><code>var parent = myContainer.getParent();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Change le nom du conteneur</td>
      <td style="text-align:left"><code>myContainer.setName(&quot;new name&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setCollapsed(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Modifiez l'état d'affaissement du conteneur, s'il peut être affaissé.</td>
      <td
      style="text-align:left"><code>myContainer.setCollapsed(false);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">Il s'agit de l'identificateur de nom de l'objet, comme vous le feriez dans un
        script.</td>
      <td style="text-align:left"><code>script.log(myContainer.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">C'est le &quot;joli nom&quot ; de l'objet, tel que vous le voyez dans le
        Inspecteur.</td>
      <td style="text-align:left"><code>script.log(myContainer.niceName);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">Ceci ajoutera un déclencheur (bouton).</td>
      <td style="text-align:left"><code>var myTrigger = myContainer.addTrigger(&quot;My Trigger&quot ;, &quot;Trigger description&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">Cela ajoutera un paramètre de nombre flottant (curseur).</td>
      <td style="text-align:left"><code>var myFloatParam = myContainer.addFloatParameter(&quot;My Float Param&quot ;,&quot;Description de mon flotteur param&quot ;,.1,0,1);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre de nombre entier (step), valeur par défaut de 2, avec un
        se situent entre 0 et 10</td>
      <td style="text-align:left"><code>var myIntParam = myContainer.addIntParameter(&quot;My Int Param&quot ;,&quot;Description de mon int param&quot ;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre booléen (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = myContainer.addBoolParameter(&quot;My Bool Param&quot ;,&quot;Description of my bool param&quot ;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre de chaîne (champ de texte)</td>
      <td style="text-align:left"> <code>var myStringParam = myContainer.addStringParameter(&quot;My String Param&quot ;,&quot;Description de ma chaîne param&quot ;, &quot;cool&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>ajouter un paramètre de couleur (sélecteur de couleur).</p>
        <Vous pouvez soit définir la couleur par défaut avec une valeur hexadécimale ARGB, [r,g,b,a] float
          ou r,g,b,a des valeurs séparées. Les valeurs r, g et b sont toujours comprises entre
          0 et 1 et alpha est facultatif (vous pouvez spécifier r,g,b seulement);</p>
      </td>
      <td style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot ;,&quot;Description of my color param&quot ;,0xff0000ff) ; //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot ;,&quot;Description of my color param&quot ;,[1,0,1]) ; //prévoyance violette</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 2d paramètre</td>
      <td style="text-align:left"><code>var myP2DParam = myContainer.addPoint2DParameter(&quot;My P2D Param&quot ;,&quot;Description of my p2d param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 3d paramètre</td>
      <td style="text-align:left"><code>var myP3DParam = myContainer.addPoint3DParameter(&quot;My P3D Param&quot ;,&quot;Description of my p3d param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre cible (pour référencer un autre paramètre)</td>
      <td style="text-align:left"><code>var myTargetParam = myContainer.addTargetParameter(&quot;My Target Param&quot ;,&quot;Description of my target param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description, </em>[directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un paramètre de fichier (pour référencer le fichier ou le dossier sur le disque).</p>
        <p>Si le mode répertoire est réglé sur vrai, un dossier au lieu d'un fichier peut être sélectionné.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = myContainer.addFileParameter(&quot;My File Param&quot ;,&quot;Description de mon fichier param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un paramètre d'énumération (menu déroulant avec options)</p>
        <p>Chaque paire de valeurs après les 2 premiers arguments définit une option et son
          données liées</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = myContainer.addEnumParameter(&quot;My Enum Param&quot ;,&quot;Description of my enum param&quot ;, &quot;Option 1&quot ;, 1,&quot;Option 2&quot ;, 5, &quot;Option 3&quot ;, &quot;banana&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addContainer(</b>name<b>)</b>
      </td>
      <td style="text-align:left">Ajouter un conteneur à l'intérieur du conteneur.</td>
      <td style="text-align:left"><code>var childContainer = myContainer.addContainer(&quot;My Child Container&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeContainer(</b>name<b>)</b>
      </td>
      <td style="text-align:left">Supprimer un conteneur enfant du conteneur.</td>
      <td style="text-align:left"><code>myContainer.removeContainer (myChildContainer)</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeParameter(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Supprimer un paramètre du conteneur.</td>
      <td style="text-align:left"><code>myContainer.removeParameter (myChildParameter);</code>
      </td>
    </tr>
  </corps>
</table>### Directeur

Les gestionnaires sont des types particuliers de conteneurs. Dans le logiciel, vous pouvez voir qu'un conteneur est un gestionnaire lorsqu'il y a une icône "**+**" à droite de son bloc. Dans la plupart des cas, il s'agit simplement de conteneurs améliorés. La plupart du temps, les gestionnaires qui vous intéresseront sont le **gestionnaire de modules, le gestionnaire de séquences, les gestionnaires de couches et les gestionnaires de clés d'automatisation.**

Lorsque vous manipulez un gestionnaire, vous avez accès à des fonctions et des propriétés spécifiques comme l'ajout d'éléments, la suppression d'éléments ou l'obtention d'un tableau de ses éléments.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>addItem(</b><em>[type]</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajoute un élément au gestionnaire et le renvoie.</p>
        <p>Certains gestionnaires comme le gestionnaire de modules ou le gestionnaire de couches peuvent créer
          plusieurs types d'articles. Ils ont donc besoin d'un type d'article à créer, qui
          vous devez définir dans le <em><b>type</b></em> argument.</p>
        <p> D'autres gestionnaires comme le gestionnaire de séquences ne sont pas nécessaires
          car il n'y a qu'un seul type de séquence. Dans ces cas, vous ne&apos;t
          doit fournir un argument lors de l'appel de la fonction.</p>
      </td>
      <td style="text-align:left">
        <p><code>var newOSCModule = root.modules.addItem(&quot;OSC&quot ;);</code>
        </p>
        <p><code>var newSequence = root.sequences.addItem();</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeItem(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Supprime un élément. <em><b>item</b></em> doit être un élément géré par ce gestionnaire.</td>
      <td
      style="text-align:left"><code>root.modules.removeItem (myModule);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItems()</b>
      </td>
      <td style="text-align:left">Retourne un tableau contenant tous les éléments de ce gestionnaire.</td>
      <td style="text-align:left">
        <p><code>var items = root.sequences.getItems();</code>
        </p>
        <p><code>script.log(&quot;Num séquences : &quot;+items.length);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemWithName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne le premier élément trouvé avec <em><b>nom. </b></em>Ceci va rechercher
        pour une correspondance exacte entre niceName, shortName et la version minuscule.</td>
      <td
      style="text-align:left"><code>var introSeq = root.sequences.getItemWithName (&quot;Intro&quot ;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAt(</b><em>index</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l'élément à l'index <em><b>de </b></em>
      </td>
      <td style="text-align:left"><code>var curSequence = root.sequences.getItemAt(1) ; //0 est le premier, ce qui permet d'obtenir la deuxième séquence de la liste.</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemIndex(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l'index de l'élément spécifié <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var index= root.sequences.getItemIndex (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemBefore(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l'élément avant l'élément spécifié <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var prevSequence = root.sequences.getItemBefore (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAfter(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l'élément après le <em><b>item.</b></em> spécifié
      </td>
      <td style="text-align:left"><code>var nextSequence = root.sequences.getItemAfter (curSequence);</code>
      </td>
    </tr>
  </corps>
</table>### Objet de script

L'objet script fait référence au conteneur de script. Vous pouvez ajouter vos propres paramètres personnalisés ici, ainsi que des informations de journalisation, des avertissements et des erreurs.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">Ceci ajoutera un déclencheur (bouton)</td>
      <td style="text-align:left"><code>var myTrigger = script.addTrigger(&quot;My Trigger&quot ;, &quot;Trigger description&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">Cela ajoutera un paramètre de nombre flottant (curseur).</td>
      <td style="text-align:left"><code>var myFloatParam = script.addFloatParameter(&quot;My Float Param&quot ;,&quot;Description of my float param&quot ;,.1,0,1);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre de nombre entier (step), valeur par défaut de 2, avec un
        se situent entre 0 et 10</td>
      <td style="text-align:left"><code>var myIntParam = script.addIntParameter(&quot;My Int Param&quot ;,&quot;Description of my int param&quot ;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre booléen (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = script.addBoolParameter(&quot;My Bool Param&quot ;,&quot;Description of my bool param&quot ;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre de chaîne (champ de texte)</td>
      <td style="text-align:left"> <code>var myStringParam = script.addStringParameter(&quot;My String Param&quot ;,&quot;Description de ma chaîne param&quot ;, &quot;cool&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>ajouter un paramètre de couleur (sélecteur de couleur).</p>
        <Vous pouvez soit définir la couleur par défaut avec une valeur hexadécimale ARGB, [r,g,b,a] float
          ou r,g,b,a des valeurs séparées. Les valeurs r, g et b sont toujours comprises entre
          0 et 1 et alpha est facultatif (vous pouvez spécifier r,g,b seulement);</p>
      </td>
      <td style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot ;,&quot;Description of my color param&quot ;,0xff0000ff) ; //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot ;,&quot;Description of my color param&quot ;,[1,0,1]) ; //prévoyance violette</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 2d paramètre</td>
      <td style="text-align:left"><code>var myP2DParam = script.addPoint2DParameter(&quot;My P2D Param&quot ;,&quot;Description of my p2d param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 3d paramètre</td>
      <td style="text-align:left"><code>var myP3DParam = script.addPoint3DParameter(&quot;My P3D Param&quot ;,&quot;Description of my p3d param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un paramètre cible (pour référencer un autre paramètre)</td>
      <td style="text-align:left"><code>var myTargetParam = script.addTargetParameter(&quot;My Target Param&quot ;,&quot;Description of my target param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description, </em>[directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un paramètre de fichier (pour référencer le fichier ou le dossier sur le disque).</p>
        <p>Si le mode répertoire est réglé sur vrai, un dossier au lieu d'un fichier peut être sélectionné.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = script.addFileParameter(&quot;Mon fichier param&quot ;,&quot;Description de mon fichier param&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>ajouter un paramètre de type énumération (menu déroulant avec options)</p>
        <p>Chaque paire de valeurs après les 2 premiers arguments définit une option et son
          données liées</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = script.addEnumParameter(&quot;My Enum Param&quot ;,&quot;Description of my enum param&quot ;, &quot;Option 1&quot ;, 1,&quot;Option 2&quot ;, 5, &quot;Option 3&quot ;, &quot;banana&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>log(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Journalise un message (doit activer &quot;Log&quot ; dans les paramètres du script)</td>
      <td
      style="text-align:left"><code>script.log(&quot;Ceci est un message&quot ;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logWarning(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Journalise un message en guise d'avertissement</td>
      <td style="text-align:left"><code>script.logWarning(&quot;Ceci est un avertissement&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logError(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Enregistre un message comme une erreur</td>
      <td style="text-align:left"><code>script.logError(&quot;This is an error&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setUpdateRate(</b><em>rate</em><b>)</b>
      </td>
      <td style="text-align:left">Définit la vitesse à laquelle la fonction update() est appelée</td>
      <td style="text-align:left"><code>script.setUpdateRate(50);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>fonction scriprtParameterChanged(</b><em>param</em><b>)</b>
      </td>
      <td style="text-align:left">Cette fonction sera appelée chaque fois qu'un paramètre de ce script aura
        changed.</td>
      <td style="text-align:left"><code>fonction scriptParameterChanged(param){ script.log(&quot;Param changed : &quot;+param.name) ; }</code>
      </td>
    </tr>
  </corps>
</table>### Objet racine

L'objet racine fait référence au moteur de Chataigne, qui est l'objet racine de tous les parents.  
Il permet d'accéder à n'importe quel objet dans la hiérarchie de Chataigne. La meilleure façon d'y accéder est de cliquer avec le bouton droit de la souris sur l'interface utilisateur d'un paramètre et de sélectionner "Copy Script control address". Vous pouvez alors passer l'adresse dans votre script et vous pourrez contrôler ce paramètre.

### Objet local

L'objet local dépend de l'endroit où les scripts sont exécutés.

* Si le script est exécuté dans un module, la variable locale fera référence au module. Vous pouvez trouver toutes les fonctions du module dans la section [Scripts de module](module-scripts.md). 
* Si le script s'exécute dans une condition, la variable locale fera référence à la condition. Vous pouvez trouver toutes les fonctions de la condition dans la section [Condition Scripts](condition-scripts.md). 
* Si le script s'exécute à l'intérieur d'un filtre, la variable locale fera référence au filtre. Vous pouvez trouver toutes les fonctions de filtrage dans la section [Filter Scripts](filter-scripts.md)[ ](condition-scripts.md)*.

### **Util objet**

L'objet utilitaire fournit des aides et des fonctions utilitaires comme le temps ou la conversion.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Méthode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <corps>
    <tr>
      <td style="text-align:left"><b>getTime()</b>
      </td>
      <td style="text-align:left">Retourne le temps écoulé depuis le démarrage du système en secondes</td>
      <td style="text-align:left"><code>var time = util.getTime();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getTimestamp()</b>
      </td>
      <td style="text-align:left">Retourne le temps depuis le 1er janvier 1970 en secondes</td>
      <td style="text-align:left"><code>var timestamp = util.getTimestamp();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getFloatFromBytes(</b><em>byte1, byte2, byte3, byte4</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un flotteur de 4 octets (big endian, l'octet 1 est le plus significatif)</td>
      <td
      style="text-align:left"><code>var value = util.getFloatFromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt32FromBytes(</b><em>byte1, byte2, byte3, byte4</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un entier de 32 bits à partir de 4 octets (big endian, l'octet 1 est le plus significatif)</td>
      <td
      style="text-align:left"><code>var value = util.getInt32FromBytes(0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt64FromBytes(</b><em>byte1, byte2, byte3, byte4, byte5, byte6, byte7, byte8</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un entier de 64 bits à partir de 8 octets (big endian, l'octet 1 est le plus significatif)</td>
      <td
      style="text-align:left"><code>var value = util.getInt64FromBytes(0, 5, 7, 22, 0, 0, 2, 10);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getIPs()</b>
      </td>
      <td style="text-align:left">Retourne un tableau de toutes les adresses IP trouvées</td>
      <td style="text-align:left">
        <p><code>var ips = util.getIPs();</code>
        </p>
        <p><code>for(var i=0 ; i&lt;ips.length ; i++) { script.log(ips[i]) ; }</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>encodeHMAC_SHA1(</b><em>text, key</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne une chaîne codée HMAC-SHA1</td>
      <td style="text-align:left"><code>var encoded = util.encodeHMAC_SHA1(&quot;my text&quot ;, &quot;my key&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>toBase64(</b><em>value</em><b>);</b>
      </td>
      <td style="text-align:left">Retourne une chaîne convertie en base-64 à partir d'une chaîne utf8.</td>
      <td style="text-align:left"><code>var str64 = util.toBase64(&quot;cool&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>path,</em><b> </b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Consultez le contenu du fichier à <em><b>path</b></em>. Si <em><b>asJSON </b></em>est <em>vrai, </em>alors
        le contenu sera analysé et renvoyé sous la forme d'un Object.</td>
      <td style="text-align:left"><code>var myTextContent = util.readFile(&quot;myfile.txt&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(</b><em>path, data</em><b>, </b><em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Ecrivez le contenu d'une chaîne ou d'un Objet dans le fichier à <em><b>path</b></em> .
        Si le fichier existe, <em><b>overwriteIfExists </b></em> vous permettra de décider
        si elle doit être écrasée ou non (false par défaut).</td>
      <td style="text-align:left">
        <p><code>données variables = &quot;super&quot;;</code>
        </p>
        <p><code>util.writeFile(&quot;monfichier.txt&quot ;, données, vrai);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>createDirectory(</b><em>folderPath</em><b>)</b>
      </td>
      <td style="text-align:left">Crée un répertoire au chemin spécifié.</td>
      <td style="text-align:left"><code>util.createDirectory(&quot;path/to/dir&quot ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectProperties(</b><em>objet, includeParameters, includeObjects</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un tableau de tous les noms de propriétés de cet <em><b>objet</b></em>.
        Vous pouvez spécifier si vous voulez inclure des paramètres et/ou des objets (comme
        conteneurs) La valeur par défaut est include all.</td>
      <td style="text-align:left"><code>var propNames = util.getObjectProperties(myObject, true, false) ; //seulement get parameters</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectMetMethods(</b><em>objet</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un tableau de tous les noms de méthode de ce <em><b>objet</b></em>.</td>
      <td
      style="text-align:left"><code>var methods= util.getObjectMetMethods();</code>
        </td>
    </tr>
  </corps>
</table>
