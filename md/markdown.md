
# Markdown

## Historique

Le [Markdown][] est un langage de balisage léger créé en 2004 par [John Gruber][] et [Aaron Swartz][]. Son but est d'offrir une syntaxe facile à lire et à écrire. Un document formaté selon Markdown devrait pouvoir être publié comme tel, en texte, sans donner l’impression qu’il a été marqué par des balises ou des instructions de formatage.

Un document rédigé en Markdown peut être converti facilement en HTML. Bien que la syntaxe Markdown ait été influencée par plusieurs filtres de conversion de texte existants vers le HTML (dont *Setext1*, *atx2*, *Textile*, *reStructuredText*, *Grutatext3* et *EtText4*), la source d’inspiration principale est le format du courrier électronique en mode texte.

Markdown est un logiciel libre sous licence BSD.

## Évolution

Depuis sa création originelle, Markdown n'a pas connu d'évolution notoire de la part de ses auteurs. De plus, ce format n'a jamais été formellement standardisé.

Pourtant, un certain nombre de variantes ont vu le jour afin de pallier ce qui a été perçu comme des limitations inhérentes à une syntaxe trop simplifiée.

À titre d'exemples, on pourra citer [MultiMarkdown][] et [GitHub Flavored Markdown][]. Ce dernier est utilisé pour les articles et la documentation sur [GitHub][], mais a également été largement adopté sur plusieurs éditeurs de texte supportant le format Markdown au niveau de la coloration syntaxique ou de la prévisualisation.

Il existe aussi :

- [phpMarkdown][]
- [Pandoc][]
- [Strapdown.js][]

## Extension

Il n'y a pas de format officiel pour le Markdown mais on peut utiliser l'une des extensions suivantes :

- markdown
- mkdown
- mkdn
- mkd
- md

Il est à noter que l'extension `text` n'est pas conseillée et que l'extension la plus utilisée est celle-ci : `md`.

## Syntaxe

### Philosophie

La syntaxe Markdown est entièrement constituée de caractères de ponctuation, choisis soigneusement afin que leur apparence évoque la signification donnée par la syntaxe. Par exemple, des astérisques placés autour d’un mot donnent l’impression que l’on met \*l’emphase\* sur celui-ci.

### Insertion HTML

La syntaxe Markdown à un objectif : être utilisée comme format d’écriture pour le web.

Le format Markdown n'a pas été créé pour remplacer le HTML. Au contraire, sa syntaxe légère ne correspond en fait qu'à un très petit sous-ensemble de ce que propose le HTML. L’idée n’est pas de créer une syntaxe qui rend plus facile l’insertion de balises HTML mais plutôt de faciliter la lecture, l’écriture et l’édition du texte en prose. Le HTML est un format de publication, Markdown est un format d’écriture. C’est pour cette raison que le Markdown s’adresse uniquement à ce qui peut être convoyé par du texte.

Pour tout équivalent de balise HTML qui n’est pas couverte par la syntaxe Markdown, vous pouvez directement insérer des balises HTML dans votre texte. Il n’y a aucune raison de la précéder ou de la délimiter par des marqueurs spéciaux indiquant le passage de la syntaxe Markdown aux balises HTML ; vous écrivez tout simplement la balise là où vous le souhaitez.

Seules restrictions, les éléments HTML de type bloc (`<div>`, `<table>`, `<pre>`, `<h1>`, `<p>`, etc.) doivent être séparés du contenu environnant par des lignes vides. De plus, les balises de début et de fin ne doivent pas être indentées avec des tabulations ou des espaces. Markdown est assez intelligent pour ne pas ajouter des balises `<p>` supplémentaires (et indésirables) autour des éléments de type bloc.

A titre d'exemple, pour ajouter un tableau HTML à un article écrit en Markdown :

	Ceci est un paragraphe régulier.

	<table>
		<tr>
			<td>Ligne de tableau</td>
		</tr>
	</table>

	Un autre paragraphe régulier.

Il est à noter que le formatage Markdown n’est pas appliqué à l’intérieur de balises de type blocs HTML. C’est à dire que vous ne pouvez pas appliquer de \*l'emphase\* selon la syntaxe Markdown à l’intérieur d’un bloc `<div>` HTML.

Les éléments HTML de type en ligne (`<span>`, `<cite>`, `<del>`, etc.) peuvent être utilisés n’importe où dans un paragraphe, dans l’élément d’une liste ou dans un titre. Si vous le souhaitez, vous pouvez même utiliser des balises HTML à la place du format Markdown ; par exemple si vous préférez utiliser la balise HTML `<a>` ou `<img>` au lieu de la syntaxe Markdown pour les liens ou les images, ceci est tout à fait possible.

Contrairement aux éléments de type bloc, la syntaxe Markdown est traitée à l’intérieur des balises de type en ligne.

#### Échappement automatique

En HTML, il y a deux caractères spéciaux qui demandent un traitement spécial : le chevron `<` et l'esperluette `&`. Les chevrons ouvrants sont utilisés pour débuter les balises ; les esperluettes indiquent une entité HTML. Si vous voulez les utiliser en tant que caractères littéraux, vous devez utiliser le code HTML de ces entités, c’est à dire que vous devez écrire `&lt;` et `&amp;` (voir « Les caractères spéciaux » de la documentation GNU/Linux).

L'esperluette est particulièrement désagréable pour les blogueurs. Si vous voulez parler de « AT&T », vous devrez écrire `AT&amp;T`. Vous devrez aussi échapper les esperluettes à l’intérieur des URLs. Cela signifie que si vous voulez créer un lien vers :

	http://images.google.com/images?num=30&q=larry+bird

Vous devrez encoder l’URL comme ceci :

	http://images.google.com/images?num=30&amp;q=larry+bird

Markdown vous permet d’utiliser ces caractères de façon naturelle en prenant soin de les encoder pour vous quand c’est nécessaire. Si vous utilisez une esperluette `&` pour débuter une entité HTML, elle restera inchangée ; autrement elle sera convertie en `&amp;`.

Si vous voulez inclure le symbole de copyright dans votre article, vous pouvez écrire `&copy;` et Markdown n’y touchera pas. Mais si vous écrivez « AT&T », Markdown le convertira en : `AT&amp;T`. De la même façon, parce que le Markdown supporte le HTML intercalé, si vous utilisez les chevrons pour délimiter les balises HTML, Markdown les traitera comme tel. Mais si vous écrivez :

	4 < 5

Markdown le convertira en :

	4 &lt; 5

Cependant, à l’intérieur des blocs ou des étendues de code, les chevrons et les esperluettes seront toujours encodés automatiquement. Ceci facilite grandement l’utilisation de Markdown quand il s’agit d’écrire au sujet du HTML. Par opposition au HTML brut qui est un très mauvais format pour écrire à propos de sa propre syntaxe parce que chaque chevron `<` et esperluette `&` dans vos exemples de code doivent être échappés.

### Éléments de bloc

#### Paragraphes et sauts de ligne

Un paragraphe est simplement une ou plusieurs lignes consécutives de texte, séparées par une ou plusieurs lignes vides. Une ligne contenant uniquement des espaces ou des tabulations est considérée comme vide. Les paragraphes ne doivent normalement pas être indentés par des espaces ou des tabulations.

La règle « une ou plusieurs lignes consécutives de texte » implique que Markdown supporte les sauts de ligne manuels à l’intérieur des paragraphes. Ceci diffère beaucoup de la plupart des autres convertisseurs de texte vers le HTML qui traduisent chaque saut de ligne à l’intérieur d’un paragraphe par la balise `<br />`.

Si vous voulez vraiment insérer une balise de saut de ligne `<br />` en utilisant Markdown, vous n’avez qu’à terminer la ligne par deux espaces, ou plus, puis appuyer sur la touche <kbd>ENTRÉE</kbd>.

Ceci nécessite un peu plus d’effort pour créer une balise `<br />`, mais une règle plus simple dans le style de « chaque saut de ligne correspond à un `<br />` » ne fonctionnerait pas bien avec le Markdown. La syntaxe des blocs de citation et des listes à plusieurs paragraphes fonctionne mieux (tout en étant plus lisible) quand vous formatez vos paragraphes avec un saut de ligne à la fin de chaque ligne.

#### Titres

Markdown supporte deux syntaxes, la première est de souligner les titres en utilisant le symbole égal `=` (pour le premier niveau) ou des tirets `-` (pour le second niveau) :

	Titre de niveau 1 (balise h1)
	=============================

	Titre de niveau 2 (balise h2)
	-----------------------------

La longueur du soulignement (avec `=` ou `-`) n'a aucune importance.

La seconde possibilité, est d'utiliser des dièses `#`, entre un et six, au début de la ligne. Le nombre de dièses représente le niveau du titre voulu :

	# Titre de niveau 1 (balise h1)

	## Titre de niveau 2 (balise h2)

	###### Titre de niveau 6 (balise h6)

Il est à noter qu'il est possible de « fermer » les titres, cela ne modifiant rien. Le nombre de dièses de fermeture n’a aucune importance :

	# Titre de niveau 1 #

	## Titre de niveau 2 ##

	### Titre de niveau 3 ######

#### Blocs de citation

Comme pour le courrier électronique, Markdown utilise le caractère chevron `>` pour délimiter les blocs de citation :

	> Ceci est un bloc de citation avec deux paragraphes. Lorem ipsum dolor 
	> sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere 
	> lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, 
	> risus.
	> 
	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	> id sem consectetuer libero luctus adipiscing.

Toutefois, Markdown permet de n’écrire qu’un seul chevron `>` au début de la première ligne d’un paragraphe :

	> Ceci est un bloc de citation avec deux paragraphes. Lorem ipsum dolor 
	  sit amet, consectetuer adipiscing elit. Aliquam hendrerit mi posuere 
	  lectus. Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, 
	  risus.

	> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
	  id sem consectetuer libero luctus adipiscing.

Les blocs de citation peuvent être imbriqués en ajoutant des niveaux additionnels avec d'autres chevrons `>` :

	> Ceci est le premier niveau de citation.
	>
	> > Ceci est un bloc de citation imbriqué.
	>
	> Retour au premier niveau.

Ils peuvent également contenir d’autres éléments de Markdown, comme des titres, des listes ou des blocs de code :

	> ## Ceci est un titre.
	> 
	> 1. Ceci est le premier élément d'une liste.
	> 2. Ceci est le second élément d'une liste.
	> 
	> Voici un exemple de code :
	> 
	>	return shell_exec("echo $input | $markdown_script");

#### Listes

Markdown supporte les listes ordonnées (numérotées) et non-ordonnées (à puces).

Les listes non-ordonnées utilisent l’astérisque `*`, le plus `+`, ou encore le tiret `-` de façon tout à fait interchangeable :

	* Rouge
	* Vert
	* Bleu

Est équivalent à :

	+ Rouge
	+ Vert
	+ Bleu

Ou à :

	- Rouge
	- Vert
	- Bleu

Il est même possible de mélanger ces trois notations :

	* Rouge
	+ Vert
	- Bleu

Les listes ordonnées utilisent un nombre suivit d’un point `.` :

	1. Félin
	2. Oiseau
	3. Poisson

Il est important de noter que l’ordre des nombres n’a aucune importance. Le code HTML produit à partir de l'exemple ci-dessus sera semblable à :

	<ol>
		<li>Félin</li>
		<li>Oiseau</li>
		<li>Poisson</li>
	</ol>

Si vous écrivez la liste comme ceci :

	1. Félin
	1. Oiseau
	1. Poisson

Ou comme ici :

	3. Félin
	1. Oiseau
	8. Poisson

Le code HTML produit sera, dans tous les exemples précédents, identique. Toutefois, il est conseillé de débuter vos listes avec le numéro 1.

Les marqueurs de liste sont généralement alignés sur la marge de gauche, mais peuvent être indentés par trois espaces ou moins. Les marqueurs de liste doivent être suivis par au moins un espace ou une tabulation. De plus, il est également possible d'ajouter une indentation après chaque saut de ligne manuel :

	* Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
	  Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
	  viverra nec, fringilla in, laoreet vitae, risus.
	* Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
	  Suspendisse id sem consectetuer libero luctus adipiscing.

Ou comme ici :

	* Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
	Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
	viverra nec, fringilla in, laoreet vitae, risus.
	* Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
	Suspendisse id sem consectetuer libero luctus adipiscing.

Si les éléments de la liste sont séparés par une ligne blanche, Markdown les placera dans des balises `<p>`. Par exemple :

	* Tour de passe-passe
	* Tour de magie

Le code HTML généré sera :

	<ul>
		<li>Tour de passe-passe</li>
		<li>Tour de magie</li>
	</ul>

Alors que ceci :

	* Tour de passe-passe

	* Tour de magie

Sera généré de cette façon :

	<ul>
		<li><p>Tour de passe-passe</p></li>
		<li><p>Tour de magie</p></li>
	</ul>

Les éléments d’une liste peuvent être constitués de plusieurs paragraphes. Tous les paragraphes suivant le premier doivent alors être indentés par 4 espaces ou une tabulation :

	1. Ceci est un élément de la liste contenant deux paragraphes. 
	   Lorem ipsum dolor sit amet, consectetuer adipiscing elit. 
	   Aliquam hendrerit mi posuere lectus.

	   Vestibulum enim wisi, viverra nec, fringilla in, laoreet
	   vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
	   sit amet velit.

	2. Suspendisse id sem consectetuer libero luctus adipiscing.

Le résultat est plus lisible, mais ici aussi Markdown permet d’écrire comme ceci :

	* Ceci est un élément de la liste avec deux paragraphes.

	  Ceci est le deuxième paragraphe dans l'élément. Vous
	n'avez besoin d'indenter que la première ligne. Lorem ipsum 
	dolor sit amet, consectetuer adipiscing elit.

	* Un autre élément dans la même liste.

Pour insérer un bloc de citation dans un élément de liste, les chevrons `>` du bloc de citation doivent être indentés :

	* Un élément de la liste avec un bloc de citation :

		> Ceci est un bloc de citation
		> à l'intérieur d'une liste.

Pour insérer un bloc de code dans un élément de liste, le bloc de code doit être indenté deux fois (une fois pour la liste et une fois pour le bloc de code), ce qui représente 8 espaces ou deux tabulations :

	* Un élément de la liste avec un bloc de code :

			instruction de code

Il est à noter qu’il est possible de déclencher une liste ordonnée involontairement. Comme avec cet exemple :

	1789. La révolution française.

Une séquence nombre-point-espace au début d’une ligne produira effectivement un élément de liste. Pour éviter cet effet non désiré, vous pouvez « casser » cette séquence en échappant le point `.` à l’aide d’une barre oblique inverse `\` :

	1789\. La révolution française.

#### Blocs de code

Afin de présenter des exemples de code dans vos pages HTML, il est utile d'utiliser ce type de bloc. Ces blocs de code sont interprétés littéralement, ce qui signifie qu'aucune modification ne sera effectuée lors de la transition vers le HTML. Le Markdown enveloppe un bloc de code avec les balises suivantes : `<pre>` et `<code>`.

Pour produire un bloc de code avec Markdown, vous n’avez qu’à indenter chaque ligne d’un bloc par au moins 4 espaces ou une tabulation. Par exemple, ce texte :

	Ceci est un paragraphe normal :

		Ceci est un bloc de code.

Donnera en HTML :

	<p>Ceci est un paragraphe normal :</p>

	<pre><code>Ceci est un bloc de code.</code></pre>

Un niveau d’indentation (4 espaces ou une tabulation) est enlevé de chaque ligne du bloc de code. Par exemple, ceci :

	Voici un exemple d'AppleScript :

		tell application "Foo"
			beep
		end tell

Deviendra :

	<p>Voici un exemple d'AppleScript :</p>

	<pre><code>tell application "Foo"
		beep
	end tell
	</code></pre>

Un bloc de code se termine à la première ligne qui n’est pas indentée ou en atteignant la fin de l’article.

À l’intérieur d’un bloc de code, l'esperluette `&` et les chevrons `< >` sont automatiquement convertis en entités HTML. Ceci permet d’inclure très facilement des exemples de code HTML en utilisant Markdown. Par exemple, ceci :

	<div class="footer">
		&copy; 2004 Foo Corporation
	</div>

Sera converti en :

	<pre><code>&lt;div class="footer"&gt;
		&amp;copy; 2004 Foo Corporation
	&lt;/div&gt;
	</code></pre>

Attention : la syntaxe Markdown n’est pas traitée à l’intérieur d’un bloc de code.

#### Lignes horizontales

Vous pouvez insérer une ligne horizontale `<hr />` dans votre texte. Pour cela il est nécessaire d'utiliser au moins trois symboles parmis : les astérisques `*`, les tirets `-` ou les barres de soulignement `_`, seuls, sur une ligne. Si vous le souhaitez, des espaces peuvent être utilisés entre chaque charactère. Les lignes suivantes sont toutes valides :

	* * *

	***

	*****

	- - -

	---------------------------------------

### Éléments en ligne

#### Liens

Deux styles de liens sont possibles : les liens incorporés au texte et les liens par références. Dans les deux cas, le texte du lien est délimité par des crochets `[]`.

##### Liens incorporés

Un lien incorporé au texte est composé d'une paire de crochets `[]` où est indiqué le nom du lien, suivi d'une paire de parenthèses `()` où doit être placée l'URL du lien. Optionnellement, il est possible d'ajouter un titre entouré de guillemets droits `"` (il sera affiché au survol de la souris). Par exemple :

	Ceci est [un exemple](http://exemple.com/ "Titre") de lien incorporé.

	[Ce lien](http://autre-exemple.net/) n'a pas de titre.

Produira :

	<p>Ceci est <a href="http://exemple.com/" title="Titre">un exemple</a> de lien incorporé.</p>

	<p><a href="http://autre-exemple.net/">Ce lien</a> n'a pas de titre.</p>

Il est possible d'indiquer des ressources locale au serveur en utilisant un chemin relatif :

	Voir ma page [Description](/description/) pour plus de détails.

##### Liens par références

Les liens par références utilisent une deuxième paire de crochets à la place des parenthèses, à l’intérieur desquels vous placez une référence pour identifier le lien :

	Ceci est [un exemple][id] de lien par référence.

Il est possible d'insérer un espace entre ces deux paires de crochets :

	Ceci est [un exemple] [id] de lien par référence.

Ensuite, n’importe où dans le document, il est nécessaire de définir le lien de la référence :

	[id]: http://exemple.com/ "Titre facultatif"

Il est possible d'entourer l'URL par des chevrons `< >` :

	[id]: <http://exemple.com/> "Titre facultatif"

Il est également possible de placer le titre sur la ligne suivante et d'utiliser des espaces supplémentaires qui ne sont là qu'à titre esthétique :

	[id]: http://exemple.com/long/chemin/vers/la/ressource
		  "Titre facultatif"

Les références sont utilisées uniquement par Markdown lors du traitement, et sont supprimées du document HTML en sortie.

Les noms des références peuvent contenir des lettres, des nombres, des espaces et de la ponctuation mais ils ne sont pas sensibles à la casse. Par exemple, les deux références suivantes sont équivalentes :

	[lien][a]
	[lien][A]

Vous pouvez utiliser une référence implicite, ce qui vous permet d’omettre celle-ci, dans ce cas le lien est identifié par son nom. Utilisez simplement une paire de crochets vides :

	[Google][]

Et ensuite définissez le lien comme ceci :

	[Google]: http://www.google.com/

Ce raccourci fonctionne aussi quand vous avez plusieurs mots séparés par des espaces :

	Visitez [Daring Fireball][] pour plus d'informations.

Le lien sera définie de la manière suivante :

	[Daring Fireball]: https://daringfireball.net/

Il y a au moins trois avantages à utiliser les liens par références par rapport aux liens incorporés au texte :

1. Ils permettent de garder la lisibilité du texte car on évite d'insérer parfois des URLs très longues.
2. En cas de modification d'une URL ou d'un titre qui pointe sur plusieurs références, un seul changement est nécessaire.
3. Si les liens sont centralisés, il est plus facile et rapide de les localiser afin d'y apporter des modifications.

#### Emphase

Le Markdown accepte deux caractères pour générer les balises HTML d'emphase : l'astérisque `*` et le caractère de soulignement `_`. Du texte placé entre l'un de ces deux symboles sera entouré par l’élément HTML `<em>`. Si on double ces caractères, alors le texte sera entouré de balises `<strong>`. Par exemple :

	*astérisques simples*

	_caractères de soulignement simples_

	**astérisques doublées**

	__caractères de soulignement doublés__

Produira :

	<em>astérisques simples</em>

	<em>caractères de soulignement simples</em>

	<strong>astérisques doublées</strong>

	<strong>caractères de soulignement doublés</strong>

Vous pouvez utiliser le style que vous souhaitez, la seule restriction est que le même caractère doit être utilisé pour ouvrir et fermer l’étendue de l’emphase.

Il est à noter que l’emphase peut être interprétée au milieu d’un mot :

	un*truc*formidable

Mais si vous placez un astérisque `*` ou un caractère de soulignement `_` entre deux espaces, il sera traité littéralement comme un astérisque ou un trait de soulignement. Pour produire un astérisque littéral à un endroit où il serait autrement utilisé comme délimiteur d’emphase, vous pouvez l’échapper à l’aide d’une barre oblique inverse (reportez-vous au chapitre « Échappement ») :

	\*ce texte est entouré d'astérisques litéraux\*

#### Étendues de code

Pour indiquer une étendue de code, entourez-la de guillemets inverses <code>`</code> (ou quotes inverses). Contrairement aux blocs de code, une étendue de code signale du code à l’intérieur d’un paragraphe. Par exemple :

	Utilisez la fonction `printf()` pour afficher un message.

Produira :

	<p>Utilisez la fonction <code>printf()</code> pour afficher un message.</p>

Pour écrire des guillemets inverses dans une étendue de code, vous pouvez doubler les guillemets inverses pour ouvrir et fermer l’étendue de code :

	``Il y a un guillemet inverse (`) ici.``

Produira :

	<p><code>Il y a un guillemet inverse (`) ici.</code></p>

Les délimiteurs de l’étendue de code peuvent inclure des espaces, un après les guillemets d’ouverture, un avant ceux de fermetures. Cela vous permet de placer les caractères de guillemets inverses littéraux au début ou à la fin d'une étendue de code :

	Un guillemet inverse dans une étendue de code : `` ` ``

	Du texte délimité par des guillemets inverses dans une étendue de code : `` `foo` ``

Produira :

	<p>Un guillemet inverse dans une étendue de code : <code>`</code></p>

	<p>Du texte délimité par des guillemets inverses dans une étendue de code : <code>`foo`</code></p>

Dans une étendue de code, l'esperluette `&` et les chevrons `< >` sont encodés automatiquement en entités HTML, ce qui permet d’ajouter facilement des exemples de balises HTML. Markdown convertira ceci :

	N'utilisez pas `<blink>` s'il vous plaît.

En ceci :

	<p>N'utilisez pas <code>&lt;blink&gt;</code> s'il vous plaît.</p>

Vous pouvez écrire ceci :

	`&#8212;` est l'équivalent décimal de `&mdash;`.

Pour produire :

	<p><code>&amp;#8212;</code> est l'équivalent décimal de <code>&amp;mdash;</code>.</p>

#### Images

Afin d'insérer des images dans un document, Markdown reprends la syntaxe des liens et ses deux variantes afin d'afficher des images dans du contenu HTML.

##### Images incorporées

La syntaxe est la même que les liens incorporés au texte à la différence qu'elle commence avec un point d'exclamation `!` :

	![Texte alternatif](/chemin/vers/image.jpg)

	![Texte alternatif](/chemin/vers/image.jpg "Titre optionnel")

##### Images par références

La syntaxe pour les images par références est donc elle aussi semblable avec les liens par références et commence toujours avec un point d'exclamation `!` :

	![Texte alternatif][id]

Où « id » est le nom de la référence de l’image. Les références sont définies en utilisant la même syntaxe que celle des liens par références :

	[id]: url/vers/image.jpg "Titre optionnel"

Markdown n’a pas de syntaxe pour spécifier les dimensions d’une image ; si vous écrivez un article pour un site Internet, il est préférable d'indiquer ces valeurs et par conséquent d'utiliser des balises HTML `<img>`.

### Divers

#### Liens automatiques

Markdown permet de créer des liens « automatiquement » pour les URLs et les adresses de courrier électronique : entourez tout simplement l’adresse par des chevrons `< >` :

	<http://www.exemple.com/>

Le code HTML produit sera :

	<a href="http://www.exemple.com/">http://www.exemple.com/</a>

Les liens automatiques pour les adresses de courrier électronique reposent sur le même principe. Toutefois, Markdown exécutera, en plus, un encodage aléatoire en entités décimales et hexadécimales. Ceci permet de rendre l’adresse plus difficile à lire par les robots qui les récupèrent pour envoyer du spam. Par exemple :

	<adresse@exemple.com>

Sera converti en quelque chose de semblable à :

	<a href="&#x6d;&#x61;&#105;l&#x74;&#x6f;:a&#x64;&#114;&#101;
	&#115;&#115;&#101;&#64;&#101;&#x78;&#101;&#x6d;&#112;&#x6c;&#x65;
	.&#99;&#x6f;&#x6d;">a&#x64;&#114;&#101;&#115;&#115;&#101;&#64;
	&#101;&#x78;&#101;&#x6d;&#112;&#x6c;&#x65;.&#99;&#x6f;&#x6d;</a>

Ce qui sera affiché par le navigateur comme un lien cliquable vers « adresse@exemple.com » pourra tromper beaucoup de robots qui recherchent des adresses, mais pas tous. C’est mieux que rien, mais une adresse publiée de cette façon finira probablement par recevoir du spam un jour ou l'autre. Comme le Markdown n'a pas évolué depuis sa création, il est fort probable que cette technique soit même obsolète.

#### Échappement

Markdown permet d’utiliser une barre oblique inverse `\` pour générer des caractères littéraux qui auraient autrement une autre signification avec la syntaxe Markdown. Par exemple, si vous voulez entourer un mot avec des astérisques `*` (sans générer de balise HTML `<em>`), il faudra ajouter des barres obliques inverses devant les astérisques, comme ceci :

	\*astérisques littéraux\*

Markdown permet d’échapper les caractères suivants :

- `\` : L'antislash ou barre oblique inverse.
- <code>`</code> : Quote inverse, guillemet inverse ou accent grave.
- `*` : L'étoile ou astérisque.
- `_` : L'underscore ou caractère de soulignement.
- `#` : Le dièse.
- `+` : L'opérateur mathématique plus.
- `-` : L'opérateur mathématique moins ou tiret.
- `.` : Le point.
- `!` : Le point d'exclamation.
- `{}` : Les accolades.
- `[]` : Les crochets.
- `()` : Les parenthèses.

## GFM

Créé et utilisé par [GitHub][], cet accronyme signifie : [GitHub Flavored Markdown][]. GFM n'est pas un autre format du Markdown, il complète et affine la syntaxe de base. Cette version du Markdown est très utilisée sur la toile.

### Underscores multiples

La version originale du Markdown transforme les caractères de soulignement `_` en balises `<em>`. Par exemple le texte `wow_super_machin` serait affiché comma cela : wow<em>super</em>machin. Lors de l'écriture de code, ce caractère est souvent utilisé, notamment pour le nommage des variables. Ceci pose donc un problème récurrent et, de ce fait, GFM ne prend pas en compte les underscores au sein de phrase qui ne contiennent pas d'espaces.

### URL automatique

Les liens sont automatiquement gérés, c'est-à-dire que vous pouvez directement écrire ceci : `http://www.google.com` pour obtenir cela : <http://www.google.com>.

### Correction

Il est possible d'obtenir du texte barré en utilisant des tildes `~` pour délimiter la portion de texte : `~~erreur~~`. A la conversion les doubles-tildes seront remplacées par des balises `<del>` pour obtenir un résultat comme celui-ci : <del>erreur</del>.

### Bloc de code balisé

Comme vu précédemment, Markdown permet la création de blocs de code quand une ou plusieurs lignes sont précédées de 4 espaces ou une tabulation. GFM supporte aussi cette syntaxe mais en ajoute une nouvelle. Il est nécessaire d'entourer un bloc de code avec 3 accents graves <code>```</code>. De plus, cette méthode n'oblige pas à insérer une ligne vide avant un bloc de code comme il est nécessaire de le faire avec le Markdown original. Il est toutefois conseillé de le faire pour une plus grande lisibilité du document :

	Voici un exemple de code :

	```
	function test() {
		console.log("notice the blank line before this function?");

		Remarquez-vous la ligne blanche qui précède ce bloc de code ?
	}
	```

### Coloration syntaxique

L'utilisation de blocs de code balisé permet d'ajouter une information supplémentaire. En effet, il est possible d'indiquer le langage utilisé. Par exemple avec un code Ruby :

	```ruby
	require 'redcarpet'
	markdown = Redcarpet.new("Hello World!")
	puts markdown.to_html
	```

Github utilise [Linguist][] pour la détection et la coloration syntaxique. Pour la liste complète des langages pris en compte, veuillez vous référer au document suivant : [the languages YAML file][].

### Tableaux

Vous pouvez créer des tableaux en utilisant des pipes `|` pour diviser chaque colonne et des tirets `-` pour les en-têtes de tableau, comme ceci :

	Premier titre | Second titre
	------------- | -------------
	Cellule       | Cellule
	Cellule       | Cellule

Pour des raisons esthétiques, vous pouvez également ajouter des pipes `|` supplémentaires aux extrémités :

	| Premier titre | Second titre  |
	| ------------- | ------------- |
	| Cellule       | Cellule       |
	| Cellule       | Cellule       |

Notez que les tirets `-` dans la partie supérieure n'ont pas besoin de correspondre à la longueur du texte d'en-tête :

	| Nom | Description          |
	| ------------- | ----------- |
	| Help      | Affiche l'aide.|
	| Close     | Ferme la fenêtre.     |

Il est également possible d'inclure du Markdown dans les lignes d'un tableau :

	| Nom | Description          |
	| ------------- | ----------- |
	| Help      | ~~Affiche~~ l'aide.|
	| Close     | _Ferme_ la fenêtre.     |

Enfin, L'usage des deux points `:` situé en dessous de l'en-tête, permet de définir l'alignement du texte : aligné à gauche, au centre ou à droite :

	| Alignement à gauche | Alignement centré | Alignement à droite |
	| :------------------ |:-----------------:| -------------------:|
	| Texte à gauche      | Texte au centre   | Texte à droite      |
	| Texte à gauche      | Texte au centre   | Texte à droite      |
	| Texte à gauche      | Texte au centre   | Texte à droite      |

Si vous souhaitez utiliser un pipe `|` à l'intérieur d'une cellule d'un tableau, il faudra utiliser son code ISO `&#124;` afin d'éviter tout problème lors de la conversion du document. En effet, il est probable que l'anti-slash `\` ne suffise pas.

## phpMarkdown

Une autre extension de Markdown relativement connue est [phpMarkdown][]. Le site et sa documentation étant en français, il n'est pas utile de s'attarder ici. Sachez simplement qu'il s'agit d'un portage PHP qui ajoute son lot de nouveautés.

## Pandoc

Créé par [John MacFarlane][], [Pandoc][] permet de convertir des fichiers vers Markdown ou de Markdown vers tout un tas d'autres formats parmi lesquels on peut trouver : ePub, PDF, rtf, docx, HTML, etc. Pandoc reprend la syntaxe de Markdown et de GFM mais ajoute beaucoup de nouveautés. Il existe une traduction relativement complète, il n'est donc pas nécessaire, là non plus, de s'y attarder. [Élaboration et conversion de documents avec Markdown et Pandoc][].

## Conclusion

Il serait difficile de faire un tour complet de toutes les variantes du Markdown. Toutefois, nous avons abordé dans ce document sa syntaxe originale ainsi que d'autres qui ajoutent une série de nouveauté. Il ne vous reste plus qu'à faire un choix entre ces diverses possibilités et écrire vos prochains documents avec Markdown.

[Markdown]: http://daringfireball.net/projects/markdown/ "Markdown - Site officiel"
[John Gruber]: https://fr.wikipedia.org/wiki/John_Gruber "John Gruber - Wikipedia"
[Aaron Swartz]: http://fr.wikipedia.org/wiki/Aaron_Swartz "Aaron Swartz - Wikipedia"
[MultiMarkdown]: http://fletcherpenney.net/multimarkdown/ "MultiMarkdown - Site officiel"
[GitHub Flavored Markdown]: https://help.github.com/articles/github-flavored-markdown/ "GitHub Flavored Markdown"
[GitHub]: https://github.com "GitHub - Site officiel"
[phpMarkdown]: https://michelf.ca/projects/php-markdown/ "phpMarkdown - Site officiel"
[Pandoc]: http://johnmacfarlane.net/pandoc/ "Pandoc - Site officiel"
[Strapdown.js]: http://strapdownjs.com "Strapdown.js - Site officiel"
[Linguist]: https://github.com/github/linguist "Linguist"
[the languages YAML file]: https://github.com/github/linguist/blob/master/lib/linguist/languages.yml
[John MacFarlane]: http://johnmacfarlane.net "John MacFarlane - Site officiel"
[Élaboration et conversion de documents avec Markdown et Pandoc]: http://enacit1.epfl.ch/markdown-pandoc/# "Traduction de Pandoc"
