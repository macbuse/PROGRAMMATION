
# UGA Introduction LaTeX  2020

## Introduction

LATEX est le format standard utilisé dans le monde de l’édition mathématique. Il existe des distributions libres de LATEX pour toutes les plateformes (voir les références).

Un document au format LATEX est un texte (au format ASCII) contenant des commandes de formatage. Ces commandes servent à structurer le texte (chapitres, sections, etc.) en laissant au compilateur le soin de rendre cette structure au mieux en fonction du format de sortie (texte imprimé, fichier PDF, sortie HTML pour mettre sur un site Web). Elles gèrent aussi l’affichage des symboles mathématiques, la numérotation des chapitres (chapter), sections, sous-sections (section, subsection), les réfèrences (on place un repère nom avec label puis on se réfère à nom avec ```ref``` ou ```pageref```)

``` {.3D"verbatim"}
\label{toto} puis \ref{toto} ou \pageref{toto}
```

ou permettent de créer automatiquement la table des matières (\ -.05truein tableofcontents). Une fois saisi, le texte source LATEX doit être compilé (parfois deux fois de suite pour mettre à jour les références et la table des matières). Le compilateur ne tient pas compte de la mise en page du texte source, le nombre d’espace entre deux mots est ignoré de même que le passage à la ligne. Seuls les sauts de lignes sont interprétés comme signalant un début de paragraphe.

La syntaxe d’une commande de formatage LATEX est :

``` {.3D"verbatim"}
\command[option]{argument}
```

Il existe dix caractères réservés qui ne sont donc pas imprimés tels quels :
$ & % # _ { } \

Pour les imprimer, il faut taper :

Un espace est crée avec \ -.07truein ⊔.

``` {.3D"verbatim"}
\$ \& \% \# \_ \{ \} \circonflexe \tild \sy=
mbol{92}
```

Le passage à la ligne (changement de paragraphe) se fait en insérant une ligne vide, la ligne suivante est alors indentée1

Un espace est crée avec \ -.07truein ⊔.

--------------------------------------------------------------------

###  Choix de l'éditeur, saisie d'un premier document.

Pour éditer votre texte en LATEX, vous devez utiliser un éditeur comme pour taper le code source d’un programme. Vous pouvez utiliser n’importe quel éditeur si vous en connaissez déjà un, comme par exemple emacs (un éditeur de fichiers sources C/C++, Java, Python, LaTeX, ... très puissant mais qui nécessite un apprentissage...). Sinon, vous pouvez apprendre TexMaker qui est un environnement facilitant beaucoup l’apprentissage de LaTeX avec des raccourcis clavier compatibles Windows et des assistants et barres d’icones pour saisir les symboles mathématiques,

#### TexMaker

Recherchez Texmaker dans les programmes (menu Bureau, pour l’installer sur votre ordinateur, voir les liens en fin de document) ou ouvrez un terminal (menu Accessoires) et tapez la commande texmaker &
(Si vous avez oublié le &, tapez Ctrl-Z puis bg). Cliquez sur Nouveau puis sur Assistant dans la barre d’icones, sélectionnez utf8x au lieu de latin1 comme encodage. Ajouter ensuite la partie du texte ci-dessous entre
`\begin{document}` et `\end{document}`.

#### Editeur classique.

Téléchargez le document
www-fourier.ujf-grenoble.fr/~parisse/info/essai.tex
Ouvrez un terminal, puis éditez le document dans le terminal, par exemple avec Emacs  :
emacs essai.tex &
(Si vous avez oublié le &, tapez Ctrl-Z puis bg). Vous pouvez aussi créer un nouveau document à partir d’un fichier vide et taper les lignes suivantes (sans les commentaires qui commencent par %).


``` {.3D"verbatim"}
\documentclass[a4paper,11pt]{article}  % 11 ou =
12pt, article ou report ou book=20
\usepackage[utf8]{inputenc}            % caract=C3=A8res accentu=C3=A9s en =
UTF8
\usepackage[T1]{fontenc}               % idem
\usepackage[francais]{babel}           % fran=C3=A7ais (chapter -> chapi=
tre...)
\usepackage{graphicx}                  % graphiques
\usepackage{amsmath,amsfonts,amssymb}  % symboles AMS
\newcommand{\N}{{\mathbb{N}}}          % d=C3=A9finit la commande \N
\title{Un essai\\Stage latex M1} % d=C3=A9finit le titre (ici sur 2 lignes)
\author{Mon Nom}                       % indiquez votre nom

\begin{document}                       % d=C3=A9but du document

\maketitle                             % =C3=A9crit le titre (cf. \title et=
 \author)

\section{Calcul de $ A^P \pmod{N}$}    % un paragraphe
Soit $A \in \N$ un entier, ...         % on utilise la commande \N

\subsection{Traduction Algorithmique}  % un sous paragraphe
\label{sec:tradu}                      % d=C3=A9finit un label
L'algorithme de la puissance rapide se compose de plusieurs parties
\begin{enumerate}
\item On commence par ...
\item Ensuite ...
\end{enumerate}

\subsection{Le programme en $C^{++}$}  % un autre sous paragraphe
On a vu (section \ref{sec:tradu}) ...  % une r=C3=A9f=C3=A9rence au label

\newpage                               % nouvelle page=20
\tableofcontents                       % table des mati=C3=A8res

\end{document}                         % fin du document=20
```


Pour traduire les différentes commandes de votre texte, il faut le compiler.


#### Texmaker 

Vous devez d’abord sauver votre texte, à la souris, icone disquette ou menu Fichier -> Enregistrer ou au clavier Ctrl-S. Cliquez ensuite sur l’icone à gauche de Compilation rapide dans la barre d’icones (vous pouvez sélectionner un autre format de rendu: par exemple le format Latex et le rendu DVI, ce dernier se met à jour automatiquement). S’il y a des erreurs, elles apparaissent numérotées en-dessous, en cliquant sur le numéro, on positionne le curseur dans le texte source à l’endroit de l’erreur.


#### Éditeur classique.
Vous devez d’abord sauver votre texte, par exemple avec emacs à la souris, icone disquette ou menu Files -> Save current buffer ou au clavier en tapant (Ctrl-X Ctrl-S sous emacs). Puis compilez en tapant dans la fenêtre de commandes (Konsole ou xterm) :
latex essai
Dans emacs, vous pouvez aussi utiliser le menu Tex-> Tex file.

La compilation se fait avec traduction en un fichier essai.dvi ou, avec un arrêt à la première erreur rencontrée. Lorsque une erreur est détectée depuis emacs, un message apparait indiquant, la nature de l’erreur et la ligne où elle se situe.

Tapez sur la touche Entree pour continuer ou tapez x puis Entree pour interrompre la compilation. Corrigez votre erreur dans l’éditeur et recompilez. Si vous avez compilé avec le menu Tex->Tex file d’emacs, vous pouvez consulter le fichier essai.log pour déterminer les erreurs à corriger.

Pour visualiser votre texte avant l’impression, utilisez le menu Tex->Tex view dans emacs ou tapez dans la fenêtre de commandes :
xdvi essai &

Si la page de visualisation n’est pas mise à jour lorsque vous compilez à nouveau, vous devez quitter xdvi en tapant sur la touche q et le relancer comme ci-dessus.


### L’impression
Pour imprimer (attention ne le faites pas maintenant!), vous cliquerez dans TexMaker sur l’icone d’imprimante ou vous taperez dans le fenêtre de commandes :
dvips essai


### Créer des fichiers PDF et HTML à partir d’un source LATEX
Si vous utilisez la commande pdflatex à la place de la commande latex, le compilateur génére un fichier .pdf au format PDF (que l’on peut lire avec Acrobrat Reader ou sous Unix avec gv ou evince). On peut aussi convertir un fichier DVI en fichier PDF par la commande dvipdf.

Pour obtenir une sortie HTML, utilisez la commande hevea ou latex2html (disponible sur certains systèmes seulement).


Les environnements LATEX
Dans TexMaker, les commandes correspondantes se trouvent dans le menu LaTeX.

C’est une partie du document délimitée par:
`\begin{type d'environnement}...\end{type d'environnement}`


-   `\begin{verbatim}` ... `\end{verbatim}` : pas d’interprétation des commandes, le texte est mis en style \ -.05truein texttt (contrairement à {\ -.05truein tt...} qui met en style \ -.05truein texttt mais interpréte...)
-    `\begin{itemize}` ... `\end{i= temize}` ou=20 `\begin{enumerate}`
    ... `\end{enumerate}` :permet d’énumerer une liste ; chaque élement de la liste doit commencer par \ -.05truein item
La différence est que enumerate numérote les items
-   `\begin{center}` ... `\end{ce= nter}` permet de centrer un texte
-   `\begin{tabular}{|l|c|r|r|}` ... &lt;= code&gt;\\end{tabular} :crée un tableau. Le nombre d’arguments (ici 4) indique le nombre de colonnes. Ces arguments définissent l’alignement l (left),c (center), r (right). On tape les lignes du tableau en séparant les colonnes par &. Chaque ligne est terminée par la commande \ -.07truein\ . Si on écrit la commande \ -.05truein hline après une fin de ligne, cela affichera un trait de séparation horizontal, Pour les traits de séparation verticaux, utiliser | dans l’argument.
-  “Exception”: pour mettre une partie de texte en italique, on écrit `{\textit ... }`, en gras `{\bf ...}`.

## L’environnement mathématique
Dans TexMaker, les commandes correspondantes se trouvent dans le menu

### Le mode mathématique
Dans le corps d’un texte, les formules mathématiques sont délimitées par un dollar, alors que les formules devant apparaître sur une ligne séparée sont délimitées par deux dollars. On tape par exemple :

``` {.3D"verbatim"}
 $x+y=0$ =
et $x-y=2$.
```

et on obtient :

```math
x+y=0```


alors que si on tape :

``` {.3D"verbatim"}
 Consid=C3=A9rons les =C3=A9quations \[x+y=3D0 =
\ \mbox{et} \ x-y=3D2\]
```

on obtient (la commande [\\ -.= 05truein
mbox]{style="3D"font-family:monospace""} permet d=E2=80=99=C3=A9crire=20
du texte dans une formule) :

Consid=C3=A9rons les =C3=A9quations

  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------
  [x]{style="3D"font-style:italic""}+[y]{styl="e=3D"font-style:italic""}=3D0  et  [x]{style="=3D"font-style:italic""}=E2=88=92[y= ]{style="3D"font-style:italic""}=3D2
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------

On peut aussi obtenir une =C3=A9quation num=C3=A9rot=C3= =A9e avec
l=E2=80=99environnement `equation` :

``` {.3D"verbatim"}
\begin{equation} \label{eq:def_x}
x =3D \sqrt{y+z}
\end{equation}
```

ce qui donne :\

+-----------------+-----------------+-----------------+-----------------+
|  [ ]{#3D"eq:def | [=E2=88=9A]{sty |   ------------- |     (1)         |
| _x"}            | le="3D"font-siz | --------------- |                 |
| [x]{style="3D"f | e:x-large""}    | --------------- |                 |
| ont-style:itali |                 | --------------- |                 |
| c""} =3D        |                 | ------------    |                 |
|                 |                 |   [y]{style="3D |                 |
|                 |                 | "font-=" italic |                 |
|                 |                 | "=""}+[z]{style |                 |
|                 |                 | ="3D"font-style |                 |
|                 |                 | :italic""}      |                 |
|                 |                 |   ------------- |                 |
|                 |                 | --------------- |                 |
|                 |                 | --------------- |                 |
|                 |                 | --------------- |                 |
|                 |                 | ------------    |                 |
+-----------------+-----------------+-----------------+-----------------+

### 4.2  Les fractions {#3D"sec14" .3D"subsection"}

Une fraction s=E2=80=99obtient avec la commande=20 [\\ -.05truein
frac]{style="3D"font-family:monospace""} ([\\ -.05truein
overline]{style="=3D"font-family:monospace""} surligne)

``` {.3D"verbatim"}
\[\frac{x}{2y}=3D0.4\overline{230769}\]
```

donne :

  ----------------------------------------
  [x]{style="3D"font-style=" italic"=""}
  2[y]{style="3D"font-st=" italic"=""}
  ----------------------------------------

=3D0.4

230769

### 4.3  Les indices, les expos= ants et les fl=C3=A8ches de vecteurs {#3D"sec15" .3D"subsection"}

Les indices s=E2=80=99obtiennent avec le caract=C3=A8re \_ , les
exposants a= vec le caract=C3=A8re et les fl=C3=A8ches de vecteurs avec
la commande [\\ -.05truein
overrightarrow]{style="3D"font-family:monospace""}

Exemple :

``` {.3D"verbatim"}
\[x_1=3D{(a^2+b^2)}^\frac{ 1 }{2}\]
\[\overrightarrow{OA_{1,i}}=3Dx^{2t}\cdot \overrightarrow{OB_i}\]
```

donne :

+-----------------------------------+-----------------------------------+
| [=                                | +-------------------------------- |
| x]{style="3D"font-style:italic""} | --------------------------------- |
| ~1~=3D([a]{style="3D"font-style:i | ------+                           |
| talic""}2+[b]{style="3D"font-styl | |   -----                         |
| e:italic""}^2^)                   |                                   |
|                                   |       |                           |
|                                   | |    1                            |
|                                   |                                   |
|                                   |       |                           |
|                                   | |   2                             |
|                                   |                                   |
|                                   |       |                           |
|                                   | |   -----                         |
|                                   |                                   |
|                                   |       |                           |
|                                   | +-------------------------------- |
|                                   | --------------------------------- |
|                                   | ------+                           |
|                                   | |                                 |
|                                   |                                   |
|                                   |       |                           |
|                                   | +-------------------------------- |
|                                   | --------------------------------- |
|                                   | ------+                           |
+-----------------------------------+-----------------------------------+

------------------------------------------------------------------------

=E2=96=B8

[OA]{sty="le=3D"font-style:italic""}~1,[=\ i]{style="3D"font-style:italic""}~

 

=3D[x]{style="3D"font-style:itali="
c"=""}^2[t]{style="3D"font-style:italic""}^=C2=B7&nbs= p;

&lt;= tbody&gt;

------------------------------------------------------------------------

= =E2=96=B8

[OB]{sty="le=3D"font-style:italic""}~i&lt;=\ /span&gt;~

 

#### 4.3.1  Les racines {#3D"sec16" .3D"subsubsection"}

&lt;= !--SEC END --&gt;

Une racine s=E2=80=99obtient avec la commande :

``` {.3D"verbatim"}
\[\sqrt{x^2+1}\]
\[\sqrt[3]{x^2+1}\]
```

donne :

+-----------------------------------+-----------------------------------+
| [=                                |   ------------------------------- |
| =E2=88=9A]{style="3D"font-size:x- | ---------                         |
| large""}                          |   [x]{style="3D"font-=" italic"=" |
|                                   | "}^2^+1                           |
|                                   |   ------------------------------- |
|                                   | ---------                         |
+-----------------------------------+-----------------------------------+

+-----------------------------------+-----------------------------------+
| [=E2=                             |   ------------------------------- |
| =88=9B]{style="3D"font-size:x-lar | ---------                         |
| ge""}                             |   [x]{style="3D"font-=" italic"=" |
|                                   | "}^2^+1                           |
|                                   |   ------------------------------- |
|                                   | ---------                         |
+-----------------------------------+-----------------------------------+

#### 4.3.2  Les limites {#3D"sec17" .3D"subsubsection"}

&lt;= !--SEC END --&gt;

Une limite s=E2=80=99obtient avec la commande :=20 [\\ -.05truein lim {
...}]{style="3D"font-family:monospace""}

= Pour =C3=A9crire les fonctions math=C3=A9matiques on les fait
pr=C3=A9c=C3= =A9der de [\\ ]{style="3D"font-family:monospace""}. On
tape :

``` {.3D"verbatim"}
=20
\[\lim_{x \rightarrow +\infty} \ln (x) =3D +\infty\]
```

pour obtenir :

+-----------------------------------+-----------------------------------+
|   ------------------------------- |  ln([x]{style="3D"font-style="    |
| ----------------------------      | italic"=""}) =3D +=E2=88=9E       |
|                                   |                                   |
|   lim                             |                                   |
|   [x]{style="3D"font-sty=" italic |                                   |
| "=""} =E2=86=92 +=E2=88=9E        |                                   |
|   ------------------------------- |                                   |
| ----------------------------      |                                   |
+-----------------------------------+-----------------------------------+

### 4.4  Les matrices {#3D"sec18" .3D"subsection"}

``` {.3D"verbatim"}
\[\left(\begin{array}{ccc}
 2 & 3 & 4\\ x & x^2 & x^3\\ 5 & 6 & 7
\end{array}\right)\]
```

donne=20

+-----------------------+-----------------------+-----------------------+
| =E2=8E=9B\            |   ------------------- | =E2=8E=9E\            |
| =E2=8E=9C\            | ---------------- ---- | =E2=8E=9F\            |
| =E2=8E=9C\            | --------------------- | =E2=8E=9F\            |
| =E2=8E=9D             | -------------- ------ | =E2=8E=A0             |
|                       |    2                  |                       |
|                       |                  3    |                       |
|                       |                       |                       |
|                       |                = 4    |                       |
|                       |   [x]{style="3D"font- |                       |
|                       | =" italic"=""}   [x]{ |                       |
|                       | style="3D"font-style: |                       |
|                       | italic""}^2^   x^3^   |                       |
|                       |   5                   |                       |
|                       |                  6    |                       |
|                       |                       |                       |
|                       |                7      |                       |
|                       |   ------------------- |                       |
|                       | ---------------- ---- |                       |
|                       | --------------------- |                       |
|                       | -------------- ------ |                       |
+-----------------------+-----------------------+-----------------------+

### 4.5  Les int=C3=A9grales et= les s=C3=A9ries {#3D"sec19" .3D"subsection"}

``` {.3D"verbatim"}
\[\int_a^b f(t)=
 \; dt\]
```

donne

+-----------------------+-----------------------+-----------------------+
| =E2=88=AB             |   ------------------- |  [f]{style="3D"font-s |
|                       | --------------------- | tyle:it="             |
|                       |   [b]{style="3D"font- | alic"=""}([t]{style=" |
|                       | style:italic""}=      | 3D"font-style:italic" |
|                       |                       | "})  dt               |
|                       |   \                   |                       |
|                       |   \                   |                       |
|                       |                       |                       |
|                       |   [a]{style="3D"font- |                       |
|                       | style=" italic"=""}   |                       |
|                       |   ------------------- |                       |
|                       | --------------------- |                       |
+-----------------------+-----------------------+-----------------------+

\

``` {.3D"verbatim"}
$\sum_{i=3D0}^{+\infty} \frac{1}{i^2}$ et \[\su=
m_{i=3D0}^{+\infty} \frac{1}{i^2}\]
```

donne : =E2=88=91~[i]{style="3D"font-style:italic""}=\ =3D0~^+=E2=88=9E^
1/i^2^ et

+-----------------------+-----------------------+-----------------------+
|   ------------------- |                       |                       |
| --------------------- |                       |                       |
| --------              |                       |                       |
|   +=E2=88=9E          |                       |                       |
|   [=E2=88=91]{style=" |                       |                       |
| 3D"font-siz=" xx-larg |                       |                       |
| e"=""}                |                       |                       |
|   [i]{style="3D"font- |                       |                       |
| sty=" italic"=""}=3D0 |                       |                       |
|   ------------------- |                       |                       |
| --------------------- |                       |                       |
| --------              |                       |                       |
+-----------------------+-----------------------+-----------------------+
| 1                     |                       |                       |
+-----------------------+-----------------------+-----------------------+
|                       |                       |                       |
+-----------------------+-----------------------+-----------------------+
| [i]{style="3D"font-st |                       |                       |
| y="                   |                       |                       |
| italic"=""}^2^        |                       |                       |
+-----------------------+-----------------------+-----------------------+

 

### 4.6  Les deriv=C3=A9es {#3D"sec20" .3D"subsection"}

=

On utilise la commande [\\ -.05truein p=
rime]{style="3D"font-family:monospace""} ou
[=E2=80=99]{style="3D"font-family:monospace""}

``` {.3D"verbatim"}
\[ f'(x)=3D(\exp(2x))^\prime=3D2\exp(2x)\]
```

donne

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
   [f]{style="3D"font-style:italic""}= =E2=80=B2([x]{style="3D"font-style:italic""})=3D(exp(2[x]{style="=3D"font-style:italic""}))^=E2=80=B2^=3D2exp(2[x]{style="=3D"font-style:italic""})
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Pour la d=C3=A9riv=C3=A9e seconde, utiliser `f'{'}`. Pour les
deriv=C3=A9es partielles on utilise [\\ -.05truein
partial]{style="3D"font-family:mon=" ospace"=""} :

``` {.3D"verbatim"}
\[ \frac{\partial f(x,y)}{\partial x}=3D2\exp(2=
x)\]
```

donne

+-----------------------+-----------------------+-----------------------+
|                       |   ------------------- | =3D2exp(2[x]{style="3 |
|                       | --------------------- | D"font-style="        |
|                       | --------------------- | italic"=""})          |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | -----                 |                       |
|                       |   =E2=88=82&= nbsp;[f |                       |
|                       | ]{style="3D"font-styl |                       |
|                       | e:italic""}([x]{style |                       |
|                       | ="3D"font-style:i=" t |                       |
|                       | alic"=""},[y]{style=" |                       |
|                       | 3D"font-style:italic" |                       |
|                       | "})                   |                       |
|                       |   =E2=88=82 [x]{st="y |                       |
|                       | le=3D"font-style:ital |                       |
|                       | ic""}                 |                       |
|                       |   ------------------- |                       |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | --------------------- |                       |
|                       | -----                 |                       |
+-----------------------+-----------------------+-----------------------+

5  =C3=89nonc=C3=A9s {#3D"sec21" .3D"section"}
--------------------

Pour mettre en valeur th=C3=A9or=C3=A8mes, propositions, lemmes et
autres corollaires, on cr=C3=A9e des environnements avec la commande=20
`newtheorem`. Ces environnements peuvent partager le m=C3=AAme compteur
ou avoir des compteurs s=C3=A9par=C3=A9s. On saisit au d=C3=A9but = du
document :

``` {.3D"verbatim"}
\newtheorem{thm}{Th=C3=A9or=C3=A8me}
\newtheorem{prop}[thm]{Proposition}
\newtheorem{defn}{D\'efinition}
```

Ici, `thm` et `prop` partagent le m=C3=AAme = compteur, mais pas `defn`.

Puis pour cr=C3=A9er un =C3=A9nonc=C3=A9, on tape=\
`\begin{thm}`\
`` \'Enonc\'e du th\'eor\`eme ``\
`\end{thm}`\
et on obtient

<div class="3D"theorem"">

[Th=C3=A9or=C3= =A8me 1]{style="3D"font-weight:bold""}  
*=C3=89nonc=C3=A9 du th=C3=A9or=C3=A8me*

</div>

6  R=C3=A9f=C3=A9rences et cit= ations {#3D"sec22" .3D"section"}
--------------------------------------

On cr=C3=A9e explicitement une r=C3=A9f=C3=A9rence avec la commande
`\= label{}` et un nom de label entre les accolades. La
r=C3=A9f=C3=A9rence correspond au n= um=C3=A9ro de section, sauf si on
se trouve dans une environnement d=E2=80=99=C3=A9quatio= n
num=C3=A9rot=C3=A9e.=20 On y fait ensuite r=C3=A9f=C3=A9rence avec la
commande `\ref{}` (et `\pageref{}` pour indiquer l= a page).

Certaines commandes, comme `\tableofcontents` uti= lisent des
r=C3=A9f=C3=A9rences cr=C3=A9es implicitement (num=C3=A9ro de section).

Les citations d=E2= =80=99oeuvre sont en g=C3=A9n=C3=A9ral
g=C3=A9r=C3=A9es par un programme ex= terne, `bibtex` =C3=A0 partir
d=E2=80=99un fichier de base de donn=C3=A9es bibliographiques= . On
utilise les commandes (menu `LaTeX` dans Texmaker)

-   `\cite{}` pour citer une oeuvre, avec en param=C3=A8tre la r=C3=
    =A9f=C3=A9rence de l=E2=80=99oeuvre
-   `\bibliiography{}` pour indiquer l= e nom de fichier de la base de
    donn=C3=A9es bibliographique,
-   `\bibliographystyle{abbrv}` pour s= p=C3=A9cifier un style
    d=E2=80=99affichage des citations (ici `abbrv` pour
    abr=C3=A9g=C3=A9),

Exemple, on cr=C3=A9e un fichier `mabiblio.bib` contenant (dans
Texmaker, utilisez le menu `Bibliographie` pour aider la saisie)=  :

``` {.3D"verbatim"}
@ book {Leborgne,
  AUTHOR=3D"D. Leborgne",
  TITLE=3D"{Calcul diff\'erentiel et g\'eom\'etrie}",
  PUBLISHER=3D"PUF",
  YEAR=3D"1982" }
```

puis on ajoute dans le source latex une fois
`\bibliiography{= mabiblio.bib}` et `\bibliographystyle{abbrv}`, et
`\cite{Leborgne}` = autant de fois que n=C3=A9cessaire. Sauvegarder le
fichier `mabiblio.bib`.

De= puis texmaker, revenir au fichier tex, puis avant-dernier menu de la
barre d=E2=80=99outil, faire une compilation latex ou pdflatex, puis
s=C3=A9lectionner bibtex comme compilateur, compiler, puis
s=C3=A9lectionner =C3=A0 nouveau latex ou pdflatex et compiler 2 fois.
En ligne de commande, taper\
`latex essai`\
`bibtex essai`\
`latex essai`\
`latex essai`

7  Espaces, ponctuation, c=C3= =A9sure. {#3D"sec23" .3D"section"}
---------------------------------------

La philosophie de L^A^T~E~X est de laisser le compilateur= g=C3=A9rer
les espaces, cependant il peut se produire qu=E2=80=99il soit
n=C3=A9cessaire d=E2=80=99en ajouter. Les commandes `\, \ \quad \qquad`
permettent d=E2=80=99ajouter un espacement horizontal de taille de plus
en plus grande. On peut aussi utiliser `\hspace{0.3cm}` o=C3=B9
l=E2=80=99argument est une longueur (avec une unit=C3=A9) pour un
espacemen= t horizontal, `\vspace{0.2cm}` pour un espacement vertical.

= L=E2=80=99espacement en d=C3=A9but de paragraphe peut =C3=AAtre omis
par la commande `\noindent`.

La commande `\\` force un= saut de ligne, la commande `\pagebreak` force
un saut de page.

Les r=C3= =A8gles de ponctuation en fran=C3=A7ais imposent de mettre
toujours un espace apr=C3=A8s le signe de ponctuation, et d=E2=80=99en
mett= re un avant si le signe de ponctuation poss=C3=A8de deux
composantes connexes. Dans ce cas on utilise un espace ins=C3=A9cable
`~` pour =C3=A9viter que le signe de ponctuation se trouve tout seul sur
une ligne.

En principe, L^A^T~E~X sait o=C3=B9 couper d= ans un mot pour passer
=C3=A0 la ligne, mais il peut =C3=AAtre n=C3=A9cessaire de
l=E2=80=99aider,= en particulier si le mot contient des accents, on
ajoute alors des `\- pour s=C3=A9parer les syllabes du mot. `

8  Ins=C3=A9rer un graphique {#3D"sec24" .3D"section"}
----------------------------

On peut ins=C3=A9rer une image au format EPS (encapsulated
postscript)=20 dans un source L^A^T~E~X de la mani=C3=A8re suivante = ;:

``` {.3D"verbatim"}
\includegraphics[width=3D\textwidth]{image}
```

o=C3=B9 [image]{style="3D"font-family:monospace""} d=C3=A9= signe le nom
du fichier `image.eps`. On peut aussi indiquer une largeur en
centim=C3=A8tres apr=C3=A8s `width=3D`. La commande Unix
[convert]{style="3D"font-family:monospace""} perme= t de convertir une
image d=E2=80=99un autre format vers le format Encapsulated Postscript,
par exemple

``` {.3D"verbatim"}
convert image.png image.eps
```

Il faut avoir d=C3=A9clar=C3=A9 en t=C3=AAte (avant
`\begin{d= ocument}`) du fichier source :

``` {.3D"verbatim"}
\usepackage{graphicx}
```

9  Cr=C3=A9er des transparents= . {#3D"sec25" .3D"section"}
---------------------------------

Pour cr=C3=A9er des transparents, on utilise fr=C3=A9quemment la classe
de = document `beamer`. Cf. par exemple le tutoriel sur\
`http://www.tuteurs.ens.fr/logiciels/latex/beamer.html`.

10  Interaction avec des logic= iels de calcul. {#3D"sec26" .3D"section"}
-----------------------------------------------

De nombreux logiciels de calcul scientifique permettent
d=E2=80=99interagir avec L^A^T~E~X, on donne deux exemples dans cette
section= .

### 10.1  [giac/xcas]{style="3D"font-f=" monospace"=""} {#3D"sec27" .3D"subsection"}

Depuis Xcas, vous pouvez copier dans le presse-papier=20 la traduction
L^A^T~E~X d=E2=80=99une expression ou sous-expression en la
s=C3=A9lectionnant et en utilisant le raccourci Ctrl-T. On peut aussi
g=C3=A9n=C3=A9rer facilement un graphique ins=C3=A9ra= ble dans un
fichier L^A^T~E~X(menu M =C3=A0 droite du graphiq= ue, puis Exporter).

Vous pouvez compiler avec `hevea` un fichier so= urce L^A^T~E~X
contenant des commandes de calcul en un document HTML5 interactif
permettant au lecteur de modifier et/ou ex=C3=A9cuter les commandes de
calcul depuis le navigateur avec lequel il consulte le document,=20 pour
plus de d=C3=A9tails, cf.\
`http://www-fourier.ujf-grenoble.fr/~parisse/giac/test_fr.tex`
`http://www-fourier.ujf-grenoble.fr/~parisse/giac/castex.html`

Sous linux, vous pouvez g=C3=A9n=C3=A9rer les deux formats de sortie=
=20 PDF et HTML5 interactif en utilisant la commande
[icas]{style="3D"font-family=" monospace"=""} ou giac au lieu de
[pdflatex]{style="3D"font-family:monospace""}. Il suff= it de cr=C3=A9er
un document latex normal, y ajouter (juste apr=C3=A8s
`\begin{document}`) `\begin{giacjsonline}` et (juste avant
`\end{document}) \end{giacjsonline}`, puis taper des commandes telles
que `\giacinputbigmath{factor(x^10-1)}` ou `\giacinput{plot(sin(x))}`.
La compilation s=E2=80=99effectue alors depuis un terminal en tapant la
commande\
`giac nomfichier`

Enfin [pgiac]{style="3D"font-family:monospa=" ce"=""} est un programme
qui permet de faire calculer=20 automatiquement par Giac (le moteur de
calcul formel de Xcas)=20 certaines expressions d=E2=80=99un fichier
source au format L^A^T&lt;= sub&gt;EX. Voir le site de J.Michel Sarlat
pour des exemples\
`http://melusine.eu.org/syracuse/giac/`

### 10.2  [texmacs]{style="3D"font-f=" monospace"=""} {#3D"sec28" .3D"subsection"}

[texmacs]{style="3D"font-family:monospace""} est un programme perme=
ttant de saisir des documents math=C3=A9matiques avec une interface
similaire =C3=A0 celle des logiciels de traitement de texte usuels tout
en conservant une qualit=C3=A9 typographique comparable =C3=A0 L^A^T~E~=
X. Il permet d=E2=80=99importer et d=E2=80=99exporter au format L^A^T=
~E~X.=20 Il poss=C3=A8de =C3=A9galement une interface pour lancer
certains=20 logiciel de calcul (Menu Inserer, sous-menu session). Pour
lancer [texmacs]{style="3D"font-family:monospace""} sous Unix,= tapez la
commande :\
[texmacs &]{style="3D"font-family:monospace""}

### 10.3  Pour aller plus loin&lt;= /h3&gt; {#3D"sec29" .3D"subsection"}

-   Exemples de distribution LaTeX\
    Windows: miktex `http://miktex.org/`\
    Mac: `http://www.tug.org/mactex/`\
    Linux: rechercher latex sur votre gestionnaire de paquets et
    s=C3=A9lectionner par exemple texlive
-   Le site de Texmaker: `www.xm1math.net/texmaker/index_fr.html`
-   `http://fr.wikibooks.org/wiki/Programmat= ion_LaTeX`
-   `http://www.tuteurs.ens.fr/logiciels/lat= ex/`
-   Le L^A^T~E~X navigator = ;: `http://tex.loria.fr/index.html`
-   le groupe AmiTeX `http://fr.groups.yahoo.com/group/AmiTeX/`
-   hevea, traducteur vers HTML `hevea.inria.fr`
-   Le site de [texmacs]{style="3D"font-family:monospa=" ce"=""} :
    [www.texmacs= .org]{style="3D"font-family:monospace""}

------------------------------------------------------------------------

 [1](3D%22https://www-fourier.ujf-grenoble.fr/~parisse/info/l=){#3D"note1"}

:   <div class="3D"fo=" otnotetext"="">

    On peut forcer un passage =C3=A0 la ligne sans=20 indentation en
    tapant [\\ -.07truein\\ ]{style="3D"font-family:monospace""} mais
    ceci n=E2= =80=99est pas=20 recommand=C3=A9 pour la lisibilit=C3=A9
    du texte.

    </div>

------------------------------------------------------------------------

> *Ce document a =C3=A9= t=C3=A9 traduit de L^A^T~E~X par* [*H^E^&lt;=
> /span&gt;V^E^A*](3D%22http://h=)

------MultipartBoundary--x5FiFSfrUUEK9q7Y6zJBjdEAVYzXT8vnHH9UQyMsry----
Content-Type: text/css Content-Transfer-Encoding: quoted-printable
Content-Location:
cid:css-ffe29773-91dc-4fe5-9ee5-514f4ba54ba8@mhtml.blink @charset
"utf-8"; .li-itemize { margin: 1ex 0ex; } .li-enumerate { margin: 1ex
0ex; } .dd-description { margin: 0ex 0ex 1ex 4ex; } .dt-description {
margin: 0ex; } .toc { list-style: none; } .footnotetext { margin: 0ex;
padding: 0ex; } div.footnotetext p { margin: 0px; text-indent: 1em; }
.thefootnotes { text-align: left; margin: 0ex; } .dt-thefootnotes {
margin: 0em; } .dd-thefootnotes { margin: 0em 0em 0em 2em; }
.footnoterule { margin: 1em auto 1em 0px; width: 50%; } .caption {
padding-left: 2ex; padding-right: 2ex; margin-left: auto; margin=
-right: auto; } .title { margin: 2ex auto; text-align: center; }
.titlemain { margin: 1ex 2ex 2ex 1ex; } .titlerest { margin: 0ex 2ex; }
.center { text-align: center; margin-left: auto; margin-right: auto; }
.flushleft { text-align: left; margin-left: 0ex; margin-right: auto; }
.flushright { text-align: right; margin-left: auto; margin-right: 0ex; }
div table { margin-left: inherit; margin-right: inherit; margin-bottom:
2px= ; margin-top: 2px; } td table { margin: auto; } table {
border-collapse: collapse; } td { padding: 0px; } .cellpadding0 tr td {
padding: 0px; } .cellpadding1 tr td { padding: 1px; } pre { text-align:
left; margin-left: 0ex; margin-right: auto; } blockquote { margin-left:
4ex; margin-right: 4ex; text-align: left; } td p { margin: 0px; } .boxed
{ border: 1px solid black; } .textboxed { border: 1px solid black; }
.vbar { border: none; width: 2px; background-color: black; } .hbar {
border: none; height: 2px; width: 100%; background-color: black; }
.hfill { border: none; height: 1px; width: 200%; background-color:
black; } .vdisplay { border-collapse: separate; border-spacing: 2px;
width: auto; em= pty-cells: show; border: 2px solid red; } .vdcell {
white-space: nowrap; padding: 0px; border: 2px solid green; } .display {
border-collapse: separate; border-spacing: 2px; width: auto; bor= der:
none; } .dcell { white-space: nowrap; padding: 0px; border: none; }
.dcenter { margin: 0ex auto; } .vdcenter { border: 2px solid rgb(255,
128, 0); margin: 0ex auto; } .minipage { text-align: left; margin-left:
0em; margin-right: auto; } .marginpar { border: thin solid black; width:
20%; text-align: left; } .marginparleft { float: left; margin-left: 0ex;
margin-right: 1ex; } .marginparright { float: right; margin-left: 1ex;
margin-right: 0ex; } .theorem { text-align: left; margin: 1ex auto 1ex
0ex; } .part { margin: 2ex auto; text-align: center; }
------MultipartBoundary--x5FiFSfrUUEK9q7Y6zJBjdEAVYzXT8vnHH9UQyMsry------
