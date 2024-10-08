# ex08-meteo

<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <title>Lecture d’un fichier texte structuré</title>
  <style>
    html {
      line-height: 1.5;
      font-family: Georgia, serif;
      font-size: 20px;
      color: #1a1a1a;
      background-color: #fdfdfd;
    }
    body {
      margin: 0 auto;
      max-width: 36em;
      padding-left: 50px;
      padding-right: 50px;
      padding-top: 50px;
      padding-bottom: 50px;
      hyphens: auto;
      word-wrap: break-word;
      text-rendering: optimizeLegibility;
      font-kerning: normal;
    }
    @media (max-width: 600px) {
      body {
        font-size: 0.9em;
        padding: 1em;
      }
    }
    @media print {
      body {
        background-color: transparent;
        color: black;
        font-size: 12pt;
      }
      p, h2, h3 {
        orphans: 3;
        widows: 3;
      }
      h2, h3, h4 {
        page-break-after: avoid;
      }
    }
    p {
      margin: 1em 0;
    }
    a {
      color: #1a1a1a;
    }
    a:visited {
      color: #1a1a1a;
    }
    img {
      max-width: 100%;
    }
    h1, h2, h3, h4, h5, h6 {
      margin-top: 1.4em;
    }
    h5, h6 {
      font-size: 1em;
      font-style: italic;
    }
    h6 {
      font-weight: normal;
    }
    ol, ul {
      padding-left: 1.7em;
      margin-top: 1em;
    }
    li > ol, li > ul {
      margin-top: 0;
    }
    blockquote {
      margin: 1em 0 1em 1.7em;
      padding-left: 1em;
      border-left: 2px solid #e6e6e6;
      color: #606060;
    }
    code {
      font-family: Menlo, Monaco, 'Lucida Console', Consolas, monospace;
      font-size: 85%;
      margin: 0;
    }
    pre {
      margin: 1em 0;
      overflow: auto;
    }
    pre code {
      padding: 0;
      overflow: visible;
    }
    .sourceCode {
     background-color: transparent;
     overflow: visible;
    }
    hr {
      background-color: #1a1a1a;
      border: none;
      height: 1px;
      margin: 1em 0;
    }
    table {
      margin: 1em 0;
      border-collapse: collapse;
      width: 100%;
      overflow-x: auto;
      display: block;
      font-variant-numeric: lining-nums tabular-nums;
    }
    table caption {
      margin-bottom: 0.75em;
    }
    tbody {
      margin-top: 0.5em;
      border-top: 1px solid #1a1a1a;
      border-bottom: 1px solid #1a1a1a;
    }
    th {
      border-top: 1px solid #1a1a1a;
      padding: 0.25em 0.5em 0.25em 0.5em;
    }
    td {
      padding: 0.125em 0.5em 0.25em 0.5em;
    }
    header {
      margin-bottom: 4em;
      text-align: center;
    }
    #TOC li {
      list-style: none;
    }
    #TOC a:not(:hover) {
      text-decoration: none;
    }
    code{white-space: pre-wrap;}
    span.smallcaps{font-variant: small-caps;}
    span.underline{text-decoration: underline;}
    div.column{display: inline-block; vertical-align: top; width: 50%;}
    div.hanging-indent{margin-left: 1.5em; text-indent: -1.5em;}
    ul.task-list{list-style: none;}
  </style>
  <!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv-printshiv.min.js"></script>
  <![endif]-->
</head>
<body>
<header id="title-block-header">
<h1 class="title">Lecture d’un fichier texte structuré</h1>
</header>
<nav id="TOC" role="doc-toc">
<ul>
<li><a href="#contexte">Contexte</a></li>
<li><a href="#environnement-de-travail">Environnement de travail</a></li>
<li><a href="#lecture-naïve-des-données">Lecture “naïve” des données</a>
<ul>
<li><a href="#objectifs">Objectifs</a></li>
<li><a href="#informations-complémentaires">Informations complémentaires</a></li>
<li><a href="#doctests">Doctests</a></li>
</ul></li>
<li><a href="#lecture-structurée-des-données">Lecture structurée des données</a>
<ul>
<li><a href="#objectifs-1">Objectifs</a></li>
<li><a href="#informations-complémentaires-1">Informations complémentaires</a></li>
<li><a href="#doctests-1">Doctests</a></li>
</ul></li>
<li><a href="#applications">Applications</a></li>
</ul>
</nav>
<style type="text/css">
@import url("https://unpkg.com/sakura.css/css/normalize.css");
@import url("https://unpkg.com/sakura.css/css/sakura.css");
</style>
<h2 id="contexte">Contexte</h2>
<p>Un <a href="https://fr.wikipedia.org/wiki/Fichier_texte">fichier texte</a> est constitué de caractères imprimables (lettres, chiffres, ponctuation, caractères spéciaux, ...), c’est à dire représentés graphiquement par un <a href="https://fr.wikipedia.org/wiki/Glyphe">glyphe</a>. Par opposition, un <a href="https://fr.wikipedia.org/wiki/Fichier_binaire">fichier binaire</a> est un fichier qui n’est pas interprétable directement sous forme de texte : une image, un son ou encore un autre fichier compressé.</p>
<h2 id="environnement-de-travail">Environnement de travail</h2>
<p>Pour cet exercice, vous devez utiliser en priorité le fichier squelette <a href="https://perso.esiee.fr/~courivad/python/ex08-meteo.py">ex08-meteo.py</a>. IMPORTANT : Enregistrez le avec <code>Right Click + Save Link As...</code> pour conserver l’encodage.</p>
<p>Selon la convention de structuration des modules, ce fichier sera structuré en quatre parties :</p>
<ol>
<li><strong>Imports et définition des variables globales</strong> ;</li>
<li><strong>Définition des fonctions secondaires</strong> ;</li>
<li><strong>Définition de la fonction principale</strong> ;</li>
<li><strong>Appel protégé de la fonction principale</strong>.</li>
</ol>
<p>Les données utilisées pour cet exercice sont extraites de données publiques fournies par <a href="https://donneespubliques.meteofrance.fr/?fond=produit&amp;id_produit=90&amp;id_rubrique=32">Météo France</a>.</p>
<p>Elles sont stockées dans le fichier <a href="https://perso.esiee.fr/~courivad/python/ex08-meteo-data-jan-2014.csv"><code>ex08-meteo-data-jan-2014.csv</code></a>. Le fichier est encodé en <code>utf8</code>. IMPORTANT : Enregistrez le avec <code>Right Click + Save Link As...</code> pour conserver l’encodage.</p>
<h2 id="lecture-naïve-des-données">Lecture “naïve” des données</h2>
<h3 id="objectifs">Objectifs</h3>
<p>L’objectif est d’écrire une fonction <code>read_meteo_data()</code> :</p>
<ul>
<li>qui prend en argument un nom de fichier ;</li>
<li>et retourne son contenu sous la forme d’une liste de <code>n</code> chaines de caractères si le fichier comporte <code>n</code> lignes.</li>
</ul>
<p>Vérifier le bon fonctionnement de la fonction en effectuant un appel depuis <code>main()</code> et en affichant la valeur de retour (les doctests de la fonction donnent des exemples d’appel et les valeurs de retour correspondantes).</p>
<h3 id="informations-complémentaires">Informations complémentaires</h3>
<p>On parle ici de lecture “naïve” car on ne tire pas avantage de la structure des données contenues dans le fichier pour lequel:</p>
<ul>
<li><p>la première ligne contient les 6 champs utilisés pour structurer les données :</p>
<ul>
<li>le nom de la station ;</li>
<li>l’heure ;</li>
<li>le jour ;</li>
<li>le mois ;</li>
<li>l’année ;</li>
<li>la température exprimée en degrés Celsius.</li>
</ul></li>
<li><p>les autres lignes du fichier contiennent les données proprement dites, séparées par des <code>;</code>.</p></li>
</ul>
<p>Ces informations devront être prises en compte “manuellement”.</p>
<p>Utiliser la construction <code>with</code> pour ouvrir ce fichier. Penser à préciser le mode d’ouverture (lecture ou écriture ?) et l’encodage ;</p>
<p>Compte tenu de la nature de l’objet à retourner, quelle est la méthode à utiliser ? <code>read()</code>, <code>readline()</code> ou <code>readlines()</code> ?</p>
<h3 id="doctests">Doctests</h3>
<p>Une fois la fonction opérationnelle pour quelques arguments, ET SEULEMENT DANS CE CAS, lancer les doctests dans un terminal.</p>
<pre><code>$ python -m doctest ex08_meteo.py -v</code></pre>
<p>La totalité des doctests doivent réussir.</p>
<h2 id="lecture-structurée-des-données">Lecture structurée des données</h2>
<h3 id="objectifs-1">Objectifs</h3>
<p>Ecrire une fonction <code>read_csv_meteo_data()</code> :</p>
<ul>
<li>qui prend en argument un nom de fichier ;</li>
<li>et retourne son contenu sous la forme d’une liste de <code>n</code> listes de <code>m</code> chaines de caractères si le fichier comporte <code>n</code> lignes de <code>m</code> données.</li>
</ul>
<p>Vérifier le bon fonctionnement de la fonction en effectuant un appel depuis <code>main()</code> et en affichant la valeur de retour (les doctests de la fonction donnent des exemples d’appel et les valeurs de retour correspondantes).</p>
<p>Comparer le code des fonctions <code>read_meteo_data()</code> et <code>read_csv_meteo_data()</code>. Lequel vous paraît le plus concis ?</p>
<h3 id="informations-complémentaires-1">Informations complémentaires</h3>
<p>Un fichier texte peut être structuré selon une convention qui facilite la lecture des données qu’il contient. Le format <a href="https://fr.wikipedia.org/wiki/Comma-separated_values">csv (Comma Separated Values)</a> est très utilisé :</p>
<ul>
<li>la version anglo saxonne utilise la virgule <code>,</code> comme délimiteur ;</li>
<li>en français, la virgule <code>,</code> est utilisée comme séparateur décimal et le délimiteur employé est le point virgule <code>;</code>.</li>
</ul>
<p>Le fichier <code>meteo-jan-2014.csv</code> est au format <code>csv</code>. On peut tirer partie de cette structuration pour améliorer un peu la lecture des données en retournant une structure plus simple à manipuler que celle obtenue dans l’exercice précédent. Pour cela, Python utilise le module <code>csv</code>.</p>
<p>Ne pas oublier d’importer le module <code>csv</code> qui n’est pas chargé au démarrage.</p>
<p>L’ouverture du fichier est identique à la version “naïve”.</p>
<p>Lors de l’utilisation de la fonction <code>csv.reader()</code>, penser à préciser le <code>delimiter</code>.</p>
<p>D’après la documentation de cette fonction, quel est l’objet retourné à la lecture de chaque ligne ?</p>
<p>D’après la consigne quel est le type de l’objet que doit retourner <code>read_csv_meteo_data()</code> ?</p>
<h3 id="doctests-1">Doctests</h3>
<p>Une fois la fonction opérationnelle pour quelques arguments, ET SEULEMENT DANS CE CAS, lancer les doctests dans un terminal.</p>
<pre><code>$ python -m doctest ex08_meteo.py -v</code></pre>
<p>La totalité des doctests doivent réussir.</p>
<h2 id="applications">Applications</h2>
<p>L’objectif est d’écrire une fonction <code>get_meteo_data_by_day()</code> :</p>
<ul>
<li>qui prend en argument les données lues par <code>read_csv_meteo_data()</code>, un nom de station et une date au format <code>dd:mm:aaaa</code> ;</li>
<li>et retourne la liste des températures pour la date et la station concernée.</li>
</ul>
<p>Si les paramètres d’appel ne correspondent pas à des données présentes dans le fichier, la fonction doit retourner la liste vide. Le nom de la station passé en argument doit être insensible à la casse (minuscules/majuscules).</p>
<p>Au vu des données contenues dans <code>meteo-jan-2014.csv</code>, quelle est la taille de la liste attendue ?</p>
<p>Quelques indices :</p>
<ul>
<li>la liste retournée par <code>read_csv_meteo_data()</code> ne contient elle que des données ?</li>
<li>la première idée est de rechercher la ligne du fichier qui correspond aux critères de recherche. N’est-il pas plus pratique d’écarter les lignes qui ne correspondent pas ?</li>
</ul>
</body>
</html>
