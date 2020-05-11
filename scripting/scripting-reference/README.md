# Référence de scripting

Vous trouverez ici une référence quasi exhaustive sur les fonctions spécifiques de Chataigne.

{% hint style="success" %}
Les scripts dans Chataigne sont basés sur une version simplifiée de Javascript. La plupart des fonctions sont disponibles, mais certaines peuvent manquer. Si certaines fonctions vous manquent, veuillez me contacter et envisager de faire un don \([https://github.com/sponsors/benkuper](https://github.com/sponsors/benkuper)\) pour que je puisse passer plus de temps à améliorer Chataigne !
{% endhint %}

{% hint style="info" %}
Cette documentation ne montre que les fonctions que j'ai rajouté par dessus le moteur Javascript de JUCE. Pour avoir plus d'informations sur toutes les fonctions de bases disponible, tu peux regarder dans le [source code du moteur Javascript](https://github.com/benkuper/JUCE/blob/master/modules/juce_core/javascript/juce_Javascript.cpp).
{% endhint %}

## Fonctions communes

Il y a quelques fonctions communes que vous pouvez utiliser, quel que soit le type de script.

{% hint style="info" %}
Aucune des fonctions ci-dessous n'est nécessaire lors de la réalisation d'un script, ce sont juste des fonctions d'aide.  
Si vous n'en avez pas besoin, ne les ajoutez pas à votre script, car Chataigne optimisera votre script en fonction des fonctions déclarées dans celui-ci.
{% endhint %}

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>init()</b>
      </td>
      <td style="text-align:left">Si elle est pr&#xE9;sente, cette fonction sera appel&#xE9;e juste apr&#xE8;s
        le chargement du script.</td>
      <td style="text-align:left">
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
      <td style="text-align:left">
        <p>Si elle est pr&#xE9;sente, cette fonction sera appel&#xE9;e r&#xE9;guli&#xE8;rement
          au rythme sp&#xE9;cifi&#xE9; par le &quot;Taux de mise &#xE0; jour&quot;
          ; param&#xE8;tre de script.</p>
        <p>Ce param&#xE8;tre n&apos;est visible que lorsque la fonction est pr&#xE9;sente
          dans le sc&#xE9;nario. Vous pouvez &#xE9;galement modifier le taux &#xE0;
          partir du script en appelant <b>script.setUpdateRate</b><em>(rate).</em> voir
          ci-dessous pour plus d&apos;informations.</p>
      </td>
      <td style="text-align:left">
        <p><code>fonction update(deltaTime)</code>
        </p>
        <p><code>{</code>
        </p>
        <p> <code>script.log(&quot;Delta time : &quot; + deltaTime);</code>
        </p>
        <p><code>}</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>## Paramètres et Triggers 

Tous les paramètres et déclencheurs ont des méthodes communes et des méthodes spécifiques 

### Méthodes et propriétés communes

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>getParent()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>myParam.getParent();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit les param&#xE8;tres name</td>
      <td style="text-align:left"><code>myParam.setName(&quot;new name&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>D&#xE9;finit un param&#xE8;tre&apos;s attribut.</p>
        <p>Tous les param&#xE8;tres obtiennent :
          <br /><em><b>readonly :</b></em> d&#xE9;finit le param&#xE8;tre comme non modifiable</p>
        <p><em><b>description :</b></em> modifier la description de l&apos;infobulle</p>
        <p><em><b>activ&#xE9; :</b></em> activer ou d&#xE9;sactiver ce param&#xE8;tre</p>
        <p><em><b>alwaysNotify :</b></em> set the alwaysNotify flag (if true, this
          d&#xE9;clenchera des mises &#xE0; jour m&#xEA;me si la valeur fix&#xE9;e
          est la m&#xEA;me qu&apos;auparavant).
          <br />Plus d&apos;informations pour des param&#xE8;tres sp&#xE9;cifiques dans
          chaque section de param&#xE8;tres&apos;s.</p>
      </td>
      <td style="text-align:left">
        <p><code>myParam.setAttribute(&quot;readonly&quot; ,true);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;description&quot; ,&quot;new description&quot; ;);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;enabled&quot; ,false);</code>
        </p>
        <p><code>myParam.setAttribute(&quot;alwaysNotify&quot; , true);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>isParameter()</b>
      </td>
      <td style="text-align:left">retourne si la cible est un param&#xE8;tre ou un d&#xE9;clencheur</td>
      <td
      style="text-align:left"><code>var isParam = myTarget.isParameter();</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">Il s&apos;agit de l&apos;identificateur de nom de l&apos;objet, comme
        vous le feriez dans un script.</td>
      <td style="text-align:left"><code>script.log(myParam.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">C&apos;est le &quot;joli nom&quot; ; de l&apos;objet, tel que vous le
        voyez dans le Inspecteur.</td>
      <td style="text-align:left"><code>script.log(myParam.niceName);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getControlAddress (</b>[reference]<b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;adresse de contr&#xF4;le OSC de cet &#xE9;lement. Le param&#xE8;tre
        optionnel <em><b>reference </b></em>permet de sp&#xE9;cifier un &#xE9;l&#xE9;ment
        relatif &#xE0; partir duquel g&#xE9;n&#xE9;rer l&apos;adresse .</td>
      <td
      style="text-align:left"><code>script.log( myContainer.getControlAddress());</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getScriptControlAddress()</b>
      </td>
      <td style="text-align:left">Retourne l&apos;adresse de contr&#xF4;le en version script de cet &#xE9;l&#xE9;ment.</td>
      <td
      style="text-align:left"><code>script.log( myContainer.getScriptControlAddress());</code>
        </td>
    </tr>
  </tbody>
</table>###  Trigger

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **trigger\(\)** | Déclenche ce contrôle | `myTrigger.trigger();` |

### Float Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>var value = myFloatParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>myFloatParam.set(.5);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs sp&#xE9;cifiques :</p>
        <p><em><b>ui :</b></em> L&apos;interface utilisateur &#xE0; utiliser pour
          afficher ce param&#xE8;tre. Valeurs accept&#xE9;es sont : <em><b>time, slider, stepper, label</b></em>
        </p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;ui&quot; ;, &quot;time&quot; ;);</code>
      </td>
    </tr>
  </tbody>
</table>### Integer Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>var value = myIntParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>myIntParam.set(2);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs sp&#xE9;cifiques :</p>
        <p><em><b>hexMode :</b></em> Afficher la valeur en d&#xE9;cimal ou en hexad&#xE9;cimal.</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;hexMode&quot;, true);</code>
      </td>
    </tr>
  </tbody>
</table>### Boolean Parameter

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **get\(\)** | Retourne la valeur de ce paramètre | `var value = myFloatParam.get();` |
| **set\(**_value_**\)** | Définit la valeur de ce paramètre | `myFloatParam.set(.5);` |

###  String Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>var value = myStringParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left"><code>myStringParam.set(&quot;super&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs sp&#xE9;cifiques :</p>
        <p><em><b>multiline</b></em> : si le param&#xE8;tre peut &#xEA;tre multiligne</p>
        <p><em><b>pr&#xE9;fixe</b></em> : ajouter un pr&#xE9;fixe avant la valeur</p>
        <p><em><b>suffixe</b></em> : ajouter un suffixe apr&#xE8;s la valeur</p>
      </td>
      <td style="text-align:left"><code>myStringParam.setAttribute (&quot;multiline&quot; ;, true);</code>
      </td>
    </tr>
  </tbody>
</table>### Color Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre. Le r&#xE9;sultat est un tableau
        contenant [r,g,b,a], les valeurs sont comprises entre 0 et 1</td>
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
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre. Vous pouvez soit d&#xE9;finir
        la valeur avec ARGB valeur hex, [r,g,b,a] tableau flottant, ou r,g,b,a
        valeurs s&#xE9;par&#xE9;es. r, g et Les valeurs b sont toujours comprises
        entre 0 et 1 et l&apos;alpha est facultatif (vous pouvez sp&#xE9;cifier
        r,g,b seulement);</td>
      <td style="text-align:left">
        <p><code>//ceci est r&#xE9;gl&#xE9; sur cyan alpha 100%</code>
        </p>
        <p><code>myColorParam.set(0xff00ffffff);</code>
        </p>
        <p><code>myColorParam.set([0,1,1,1]);</code>
        </p>
        <p><code>myColorParam.set(0,1,1,1);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Target Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de la cha&#xEE;ne de l&apos;adresse cible</td>
      <td style="text-align:left"><code>var address = myTargetParam.get();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getTarget()</b>
      </td>
      <td style="text-align:left">Retourne la cible r&#xE9;elle s&#xE9;lectionn&#xE9;e</td>
      <td style="text-align:left"><code>var target = myTargetParam.getTarget();</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de la cha&#xEE;ne de caract&#xE8;res de l&apos;adresse
        de target&apos;s.</td>
      <td style="text-align:left"><code>myTargetParam.set (&quot;/root/modules/osc&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs sp&#xE9;cifiques :</p>
        <p><em><b>root</b></em> : le conteneur racine &#xE0; partir duquel la recherche
          doit &#xEA;tre effectu&#xE9;e</p>
        <p><em><b>searchLevel</b></em> : pr&#xE9;ciser le niveau maximum &#xE0; rechercher
          dans le root</p>
        <p><em><b>showParameters</b></em> : si la cible est contr&#xF4;lable, cacher
          ou montrer param&#xE8;tres</p>
        <p><em><b>showTriggers</b></em> : si la cible est contr&#xF4;lable, cacher
          ou montrer d&#xE9;clencheurs</p>
        <p><em><b>labelLevel</b></em> : le niveau des parents &#xE0; afficher dans
          l&apos;IU.</p>
      </td>
      <td style="text-align:left">
        <p><code>myTargetParam.setAttribute (&quot;searchLevel&quot; ;,2);</code>
        </p>
        <p><code>myTargetParam.setAttribute (&quot;root&quot; ;, root.sequences);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Enum Parameter

| Méthode | Description | Exemple |
| :--- | :--- | :--- |
| **addOption\(**_label, value_**\)** | Ajouter une option à la liste | `myEnumParam.addOption("nouvelle option",3);` |
| **get\(\)** | Obtenez le label sélectionné | `var label = myEnumParam.get();` |
| **getData\(\)** | Obtenir les données sélectionnées | `var data = myEnumParam.getData();` |
| **set\(**_label_**\)** | Définit la valeur avec l'étiquette fournie | `myEnumParam.set("nouvelle option");` |
| **removeOptions\(\)** | Supprime toutes les options. | `myEnumParam.removeOptions();` |

### File Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>setAttribute(</b><em>attribut, value</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Attributs sp&#xE9;cifiques :</p>
        <p><em><b>directoryMode </b></em>: pr&#xE9;ciser si l&apos;on veut chercher
          un fichier ou un dossier.</p>
      </td>
      <td style="text-align:left"><code>myFileParam.setAttribute (&quot;directoryMode&quot;,true);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Consultez le contenu du fichier. Si <em><b>asJSON</b></em> est <em>vrai,</em> alors
        le contenu sera analys&#xE9; et renvoy&#xE9; sous la forme d&apos;un Object.</td>
      <td
      style="text-align:left">
        <p><code>var myTextContent = myFileParam.readFile ();</code>
        </p>
        <p><code>var myJSONContent = myFileParam.readFile (true);</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(data,</b>  <em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Ecrivez le contenu ou une cha&#xEE;ne d&apos;un Objet dans le fichier
        s&#xE9;lectionn&#xE9;. Si le existe, <em><b>overwriteIfExists</b></em> vous
        permettra de d&#xE9;cider si pour l&apos;&#xE9;craser ou non (false par
        d&#xE9;faut).</td>
      <td style="text-align:left">
        <p><code>donn&#xE9;es variables = &quot;super&quot;;</code>
        </p>
        <p><code>myFileParam.writeFile (donn&#xE9;es, vrai);</code>
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
      <td style="text-align:left">Ceci lancera le fichier s&#xE9;lectionn&#xE9; avec les <em><b>arguments</b></em> fournis</td>
      <td
      style="text-align:left"><code>myFileParam.launchFile<br />(&quot;--verbose&quot; ;)</code>
        </td>
    </tr>
  </tbody>
</table>### Point2D Parameter

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre. Le r&#xE9;sultat est un tableau
        contenant [x, y].</td>
      <td style="text-align:left">
        <p><code>var value = my2dParam.get();</code>
        </p>
        <p><code>script.log(&quot;x : &quot;+value[0]);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left">
        <p><code>my2DParam.set(2, 0.5);</code>
        </p>
        <p><code>my2DParam.set([1,4.63]);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>### Point3D Parameter 

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>get()</b>
      </td>
      <td style="text-align:left">Retourne la valeur de ce param&#xE8;tre. Le r&#xE9;sultat est un tableau
        contenant [x, y, z].</td>
      <td style="text-align:left">
        <p><code>var value = my3dParam.get();</code>
        </p>
        <p><code>script.log(&quot;x : &quot;+value[0]);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>set(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la valeur de ce param&#xE8;tre</td>
      <td style="text-align:left">
        <p><code>my3DParam.set(2, 0.5, 0);</code>
        </p>
        <p><code>my3DParam.set([1,4.63, 8]);</code>
        </p>
      </td>
    </tr>
  </tbody>
</table>## Container 

Les conteneurs sont tout objet qui contient des paramètres ou d'autres récipients.   
Si vous visez un élément de la hiérarchie \( _root_ ou _local_ \), ce sera soit un conteneur, soit un paramètre. Donc si ce n'est pas un paramètre, alors c'est un conteneur.

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>getChild(</b><em>childName</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne le param&#xE8;tre ou le conteneur avec le nom fourni.</td>
      <td
      style="text-align:left"><code>var child = myContainer.getChild(&quot;activity&quot; ;);</code>
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
      <td style="text-align:left"><code>myContainer.setName(&quot;new name&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setCollapsed(</b><em>value</em><b>)</b>
      </td>
      <td style="text-align:left">Modifiez l&apos;&#xE9;tat d&apos;affaissement du conteneur, s&apos;il
        peut &#xEA;tre affaiss&#xE9;.</td>
      <td style="text-align:left"><code>myContainer.setCollapsed(false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>name</b>
      </td>
      <td style="text-align:left">Il s&apos;agit de l&apos;identificateur de nom de l&apos;objet, comme
        vous le feriez dans un script.</td>
      <td style="text-align:left"><code>script.log(myContainer.name);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>niceName</b>
      </td>
      <td style="text-align:left">C&apos;est le &quot;joli nom&quot; ; de l&apos;objet, tel que vous le
        voyez dans le Inspecteur.</td>
      <td style="text-align:left"><code>script.log(myContainer.niceName);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">Ceci ajoutera un d&#xE9;clencheur (bouton).</td>
      <td style="text-align:left"><code>var myTrigger = myContainer.addTrigger(&quot;My Trigger&quot;, &quot;Trigger description&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">Cela ajoutera un param&#xE8;tre de nombre flottant (curseur).</td>
      <td
      style="text-align:left"><code>var myFloatParam = myContainer.addFloatParameter(&quot;My Float Param&quot;,&quot;Description de mon flotteur param&quot;,.1,0,1);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de nombre entier (step), valeur par d&#xE9;faut
        de 2, avec un se situent entre 0 et 10</td>
      <td style="text-align:left"><code>var myIntParam = myContainer.addIntParameter(&quot;My Int Param&quot;,&quot;Description de mon int param&quot;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre bool&#xE9;en (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = myContainer.addBoolParameter(&quot;My Bool Param&quot;,&quot;Description of my bool param&quot;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de cha&#xEE;ne (champ de texte)</td>
      <td style="text-align:left"> <code>var myStringParam = myContainer.addStringParameter(&quot;My String Param&quot;,&quot;Description de ma cha&#xEE;ne param&quot;, &quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de couleur (s&#xE9;lecteur de couleur).</td>
      <td
      style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff) ; //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot;,&quot;Description of my color param&quot;,[1,0,1]) ; //pr&#xE9;voyance violette</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 2d param&#xE8;tre</td>
      <td style="text-align:left"><code>var myP2DParam = myContainer.addPoint2DParameter(&quot;My P2D Param&quot;,&quot;Description of my p2d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 3d param&#xE8;tre</td>
      <td style="text-align:left"><code>var myP3DParam = myContainer.addPoint3DParameter(&quot;My P3D Param&quot;,&quot;Description of my p3d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre cible (pour r&#xE9;f&#xE9;rencer un autre param&#xE8;tre)</td>
      <td
      style="text-align:left"><code>var myTargetParam = myContainer.addTargetParameter(&quot;My Target Param&quot;,&quot;Description of my target param&quot;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description,</em> [directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un param&#xE8;tre de fichier (pour r&#xE9;f&#xE9;rencer le fichier
          ou le dossier sur le disque).</p>
        <p>Si le mode r&#xE9;pertoire est r&#xE9;gl&#xE9; sur vrai, un dossier au
          lieu d&apos;un fichier peut &#xEA;tre s&#xE9;lectionn&#xE9;.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = myContainer.addFileParameter(&quot;My File Param&quot;,&quot;Description de mon fichier param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un param&#xE8;tre d&apos;&#xE9;num&#xE9;ration (menu d&#xE9;roulant
          avec options)</p>
        <p>Chaque paire de valeurs apr&#xE8;s les 2 premiers arguments d&#xE9;finit
          une option et son donn&#xE9;es li&#xE9;es</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = myContainer.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;, &quot;Option 1&quot;, 1,&quot;Option 2&quot;, 5, &quot;Option 3&quot;, &quot;banana&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addContainer(</b>name<b>)</b>
      </td>
      <td style="text-align:left">Ajouter un conteneur &#xE0; l&apos;int&#xE9;rieur du conteneur.</td>
      <td
      style="text-align:left"><code>var childContainer = myContainer.addContainer(&quot;My Child Container&quot;);</code>
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
      <td style="text-align:left">Supprimer un param&#xE8;tre du conteneur.</td>
      <td style="text-align:left"><code>myContainer.removeParameter (myChildParameter);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getControlAddress (</b>[reference]<b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;adresse de contr&#xF4;le OSC de cet &#xE9;lement. Le param&#xE8;tre
        optionnel <em><b>reference </b></em>permet de sp&#xE9;cifier un &#xE9;l&#xE9;ment
        relatif &#xE0; partir duquel g&#xE9;n&#xE9;rer l&apos;adresse .</td>
      <td
      style="text-align:left"><code>script.log( myContainer.getControlAddress());</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getScriptControlAddress()</b>
      </td>
      <td style="text-align:left">Retourne l&apos;adresse de contr&#xF4;le en version script de cet &#xE9;l&#xE9;ment.</td>
      <td
      style="text-align:left"><code>script.log( myContainer.getScriptControlAddress());</code>
        </td>
    </tr>
  </tbody>
</table>## Managers 

Les managers sont des types particuliers de conteneurs. Dans le logiciel, vous pouvez voir qu'un conteneur est un gestionnaire lorsqu'il y a une icône "**+**\*" à droite de son bloc. Dans la plupart des cas, il s'agit simplement de conteneurs améliorés. La plupart du temps, les gestionnaires qui vous intéresseront sont **le gestionnaire de modules, le gestionnaire de séquences, les gestionnaires de couches et les gestionnaires de clés d'automatisation.**  
Lorsque vous manipulez un gestionnaire, vous avez accès à des fonctions et des propriétés spécifiques comme l'ajout d'éléments, la suppression d'éléments ou l'obtention d'un tableau de ses éléments.

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>addItem(</b><em>[type]</em><b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajoute un &#xE9;l&#xE9;ment au gestionnaire et le renvoie.</p>
        <p>Certains gestionnaires comme le gestionnaire de modules ou le gestionnaire
          de couches peuvent cr&#xE9;er plusieurs types d&apos;articles. Ils ont
          donc besoin d&apos;un type d&apos;article &#xE0; cr&#xE9;er, qui vous devez
          d&#xE9;finir dans le <em><b>type</b></em> argument.</p>
        <p>D&apos;autres gestionnaires comme le gestionnaire de s&#xE9;quences ne
          sont pas n&#xE9;cessaires car il n&apos;y a qu&apos;un seul type de s&#xE9;quence.
          Dans ces cas, vous ne&apos;t doit fournir un argument lors de l&apos;appel
          de la fonction.</p>
      </td>
      <td style="text-align:left">
        <p><code>var newOSCModule = root.modules.addItem(&quot;OSC&quot;);</code>
        </p>
        <p><code>var newSequence = root.sequences.addItem();</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>removeItem(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Supprime un &#xE9;l&#xE9;ment. <em><b>item</b></em> doit &#xEA;tre un &#xE9;l&#xE9;ment
        g&#xE9;r&#xE9; par ce gestionnaire.</td>
      <td style="text-align:left"><code>root.modules.removeItem (myModule);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItems()</b>
      </td>
      <td style="text-align:left">Retourne un tableau contenant tous les &#xE9;l&#xE9;ments de ce gestionnaire.</td>
      <td
      style="text-align:left">
        <p><code>var items = root.sequences.getItems();</code>
        </p>
        <p><code>script.log(&quot;Num s&#xE9;quences : &quot;+items.length);</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemWithName(</b><em>name</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne le premier &#xE9;l&#xE9;ment trouv&#xE9; avec <em><b>nom.</b></em> Ceci
        va rechercher pour une correspondance exacte entre niceName, shortName
        et la version minuscule.</td>
      <td style="text-align:left"><code>var introSeq = root.sequences.getItemWithName (&quot;Intro&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAt(</b><em>index</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;&#xE9;l&#xE9;ment &#xE0; l&apos;index <em><b>de</b></em>
      </td>
      <td style="text-align:left"><code>var curSequence = root.sequences.getItemAt(1) ; //0 est le premier, ce qui permet d&apos;obtenir la deuxi&#xE8;me s&#xE9;quence de la liste.</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemIndex(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;index de l&apos;&#xE9;l&#xE9;ment sp&#xE9;cifi&#xE9; <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var index= root.sequences.getItemIndex (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemBefore(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;&#xE9;l&#xE9;ment avant l&apos;&#xE9;l&#xE9;ment sp&#xE9;cifi&#xE9; <em><b>item.</b></em>
      </td>
      <td style="text-align:left"><code>var prevSequence = root.sequences.getItemBefore (curSequence);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getItemAfter(</b><em>item</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne l&apos;&#xE9;l&#xE9;ment apr&#xE8;s le <em><b>item.</b></em> sp&#xE9;cifi&#xE9;</td>
      <td
      style="text-align:left"><code>var nextSequence = root.sequences.getItemAfter (curSequence);</code>
        </td>
    </tr>
  </tbody>
</table>## Objet _script_

L'objet _script_ fait référence au conteneur de script. Vous pouvez ajouter vos propres paramètres personnalisés ici, ainsi que des informations de journalisation, des avertissements et des erreurs.

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>addTrigger(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">Ceci ajoutera un d&#xE9;clencheur (bouton)</td>
      <td style="text-align:left"><code>var myTrigger = script.addTrigger(&quot;My Trigger&quot;, &quot;Trigger description&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFloatParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">Cela ajoutera un param&#xE8;tre de nombre flottant (curseur).</td>
      <td
      style="text-align:left"><code>var myFloatParam = script.addFloatParameter(&quot;My Float Param&quot;,&quot;Description of my float param&quot;,.1,0,1);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addIntParameter(</b><em>name, description, default, min max</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de nombre entier (step), valeur par d&#xE9;faut
        de 2, avec un se situent entre 0 et 10</td>
      <td style="text-align:left"><code>var myIntParam = script.addIntParameter(&quot;My Int Param&quot;,&quot;Description of my int param&quot;,2,0,10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addBoolParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre bool&#xE9;en (toggle)</td>
      <td style="text-align:left"><code>var myBoolParam = script.addBoolParameter(&quot;My Bool Param&quot;,&quot;Description of my bool param&quot;,false);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addStringParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de cha&#xEE;ne (champ de texte)</td>
      <td style="text-align:left"> <code>var myStringParam = script.addStringParameter(&quot;My String Param&quot;,&quot;Description de ma cha&#xEE;ne param&quot;, &quot;cool&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addColorParameter(</b><em>name, description, default</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre de couleur (s&#xE9;lecteur de couleur).</td>
      <td
      style="text-align:left">
        <p><code>var myColorParam = script.addColorParameter(&quot;My Color Param&quot;,&quot;Description of my color param&quot;,0xff0000ff) ; //default blue alpha 100%</code>
        </p>
        <p><code>var myColorParam2 = script.addColorParameter(&quot;My Color Param 2 &quot;,&quot;Description of my color param&quot;,[1,0,1]) ; //pr&#xE9;voyance violette</code>
        </p>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint2DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 2d param&#xE8;tre</td>
      <td style="text-align:left"><code>var myP2DParam = script.addPoint2DParameter(&quot;My P2D Param&quot;,&quot;Description of my p2d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addPoint3DParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un point 3d param&#xE8;tre</td>
      <td style="text-align:left"><code>var myP3DParam = script.addPoint3DParameter(&quot;My P3D Param&quot;,&quot;Description of my p3d param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addTargetParameter(</b><em>name, description</em><b>)</b>
      </td>
      <td style="text-align:left">ajouter un param&#xE8;tre cible (pour r&#xE9;f&#xE9;rencer un autre param&#xE8;tre)</td>
      <td
      style="text-align:left"><code>var myTargetParam = script.addTargetParameter(&quot;My Target Param&quot;,&quot;Description of my target param&quot;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addFileParameter(</b><em>name, description,</em> [directoryMode]<b>)</b>
      </td>
      <td style="text-align:left">
        <p>Ajouter un param&#xE8;tre de fichier (pour r&#xE9;f&#xE9;rencer le fichier
          ou le dossier sur le disque).</p>
        <p>Si le mode r&#xE9;pertoire est r&#xE9;gl&#xE9; sur vrai, un dossier au
          lieu d&apos;un fichier peut &#xEA;tre s&#xE9;lectionn&#xE9;.</p>
      </td>
      <td style="text-align:left"><code>var myFileParam = script.addFileParameter(&quot;Mon fichier param&quot;,&quot;Description de mon fichier param&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>addEnumParameter(</b><em>name, description, label1, value1, label2, value2, ..</em>.<b>)</b>
      </td>
      <td style="text-align:left">
        <p>ajouter un param&#xE8;tre de type &#xE9;num&#xE9;ration (menu d&#xE9;roulant
          avec options)</p>
        <p>Chaque paire de valeurs apr&#xE8;s les 2 premiers arguments d&#xE9;finit
          une option et son donn&#xE9;es li&#xE9;es</p>
      </td>
      <td style="text-align:left"><code>var myEnumParam = script.addEnumParameter(&quot;My Enum Param&quot;,&quot;Description of my enum param&quot;, &quot;Option 1&quot; ;, 1,&quot;Option 2&quot; ;, 5, &quot;Option 3&quot; ;, &quot;banana&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>log(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Journalise un message (doit activer &quot;Log&quot; ; dans les param&#xE8;tres
        du script)</td>
      <td style="text-align:left"><code>script.log(&quot;Ceci est un message&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logWarning(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Journalise un message en guise d&apos;avertissement</td>
      <td style="text-align:left"><code>script.logWarning(&quot;Ceci est un avertissement&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>logError(</b><em>message</em><b>)</b>
      </td>
      <td style="text-align:left">Enregistre un message comme une erreur</td>
      <td style="text-align:left"><code>script.logError(&quot;This is an error&quot;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>setUpdateRate(</b><em>rate</em><b>)</b>
      </td>
      <td style="text-align:left">D&#xE9;finit la vitesse &#xE0; laquelle la fonction update() est appel&#xE9;e</td>
      <td
      style="text-align:left"><code>script.setUpdateRate(50);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>fonction scriprtParameterChanged(</b><em>param</em><b>)</b>
      </td>
      <td style="text-align:left">Cette fonction sera appel&#xE9;e chaque fois qu&apos;un param&#xE8;tre
        de ce script aura changed.</td>
      <td style="text-align:left"><code>fonction scriptParameterChanged(param){ script.log(&quot;Param changed : &quot;+param.name); }</code>
      </td>
    </tr>
  </tbody>
</table>## Objet _root_

L'objet _root_ fait référence au moteur de Chataigne, qui est l'objet racine de tous les parents. Il permet d'accéder à n'importe quel objet dans la hiérarchie de Chataigne. La meilleure façon d'y accéder est de cliquer avec le bouton droit de la souris sur l'interface utilisateur d'un paramètre et de sélectionner "Copy Script control address". Vous pouvez alors passer l'adresse dans votre script et vous pourrez contrôler ce paramètre. 

## Objet _local_ 

L'objet _local_ dépend de l'endroit où les scripts sont exécutés. 

* Si le script est exécuté dans un module, la variable locale fera référence au module. Vous pouvez trouver toutes les fonctions du module dans la section [Module Scripts](module-scripts.md). 
* Si le script s'exécute dans une condition, la variable locale fera référence à la condition. Vous pouvez trouver toutes les fonctions de la condition dans la section [Condition Scripts.](condition-scripts.md) 
* Si le script s'exécute à l'intérieur d'un filtre, la variable locale fera référence au filtre. Vous pouvez trouver toutes les fonctions de filtrage dans la section [Filter Scripts](filter-scripts.md).

## Objet _util_

L'objet _util_ fournit des aides et des fonctions utilitaires comme le temps ou la conversion.

<table>
  <thead>
    <tr>
      <th style="text-align:left">M&#xE9;thode</th>
      <th style="text-align:left">Description</th>
      <th style="text-align:left">Exemple</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>getTime()</b>
      </td>
      <td style="text-align:left">Retourne le temps &#xE9;coul&#xE9; depuis le d&#xE9;marrage du syst&#xE8;me
        en secondes</td>
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
      <td style="text-align:left">Retourne un float de 4 octets (big endian, l&apos;octet 1 est le plus
        significatif)</td>
      <td style="text-align:left"><code>var value = util.getFloatFromBytes(0, 0, 2, 10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt32FromBytes(</b><em>byte1, byte2, byte3, byte4</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un entier de 32 bits &#xE0; partir de 4 octets (big endian, l&apos;octet
        1 est le plus significatif)</td>
      <td style="text-align:left"><code>var value = util.getInt32FromBytes(0, 0, 2, 10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getInt64FromBytes(</b><em>byte1, byte2, byte3, byte4, byte5, byte6, byte7, byte8</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un entier de 64 bits &#xE0; partir de 8 octets (big endian, l&apos;octet
        1 est le plus significatif)</td>
      <td style="text-align:left"><code>var value = util.getInt64FromBytes(0, 5, 7, 22, 0, 0, 2, 10);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getIPs()</b>
      </td>
      <td style="text-align:left">Retourne un tableau de toutes les adresses IP trouv&#xE9;es</td>
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
      <td style="text-align:left">Retourne une cha&#xEE;ne cod&#xE9;e HMAC-SHA1</td>
      <td style="text-align:left"><code>var encoded = util.encodeHMAC_SHA1(&quot;my text&quot;, &quot;my key&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>toBase64(</b><em>value</em><b>);</b>
      </td>
      <td style="text-align:left">Retourne une cha&#xEE;ne convertie en base-64 &#xE0; partir d&apos;une
        cha&#xEE;ne utf8.</td>
      <td style="text-align:left"><code>var str64 = util.toBase64(&quot;cool&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>readFile(</b><em>path,</em>  <em>[asJSON]</em><b>)</b>
      </td>
      <td style="text-align:left">Consultez le contenu du fichier &#xE0; <em><b>path</b></em>. Si <em><b>asJSON</b></em> est <em>vrai,</em> alors
        le contenu sera analys&#xE9; et renvoy&#xE9; sous la forme d&apos;un Object.</td>
      <td
      style="text-align:left"><code>var myTextContent = util.readFile(&quot;myfile.txt&quot;);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>writeFile(</b><em>path, data</em><b>,</b>  <em>overwriteIfExists</em><b>)</b>
      </td>
      <td style="text-align:left">Ecrivez le contenu d&apos;une cha&#xEE;ne ou d&apos;un Objet dans le fichier
        &#xE0; <em><b>path</b></em> . Si le fichier existe, <em><b>overwriteIfExists</b></em> vous
        permettra de d&#xE9;cider si elle doit &#xEA;tre &#xE9;cras&#xE9;e ou non
        (false par d&#xE9;faut).</td>
      <td style="text-align:left">
        <p><code>donn&#xE9;es variables = &quot;super&quot;;</code>
        </p>
        <p><code>util.writeFile(&quot;monfichier.txt&quot;, donn&#xE9;es, vrai);</code>
        </p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>createDirectory(</b><em>folderPath</em><b>)</b>
      </td>
      <td style="text-align:left">Cr&#xE9;e un r&#xE9;pertoire au chemin sp&#xE9;cifi&#xE9;.</td>
      <td style="text-align:left"><code>util.createDirectory(&quot;path/to/dir&quot; ;);</code>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectProperties(</b><em>objet, includeParameters, includeObjects</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un tableau de tous les noms de propri&#xE9;t&#xE9;s de cet <em><b>objet</b></em>.
        Vous pouvez sp&#xE9;cifier si vous voulez inclure des param&#xE8;tres et/ou
        des objets (comme conteneurs) La valeur par d&#xE9;faut est include all.</td>
      <td
      style="text-align:left"><code>var propNames = util.getObjectProperties(myObject, true, false) ; //seulement get parameters</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getObjectMethods(</b><em>objet</em><b>)</b>
      </td>
      <td style="text-align:left">Retourne un tableau de tous les noms de m&#xE9;thode de ce <em><b>objet</b></em>.</td>
      <td
      style="text-align:left"><code>var methods= util.getObjectMethods();</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>copyToClipboard(</b><em>data, data2...)</em>
      </td>
      <td style="text-align:left">Copie les donn&#xE9;es concat&#xE9;n&#xE9;es dans le presse-papier.</td>
      <td
      style="text-align:left"><code>util.copyToClipboard(&quot;super&quot;,5, myData);</code>
        </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>getFromClipboard(</b><em>)</em>
      </td>
      <td style="text-align:left">Retourne le contenu du presse-papier.</td>
      <td style="text-align:left"><code>var data = util.getFromClipboard();</code>
      </td>
    </tr>
  </tbody>
</table>