#  Administration Système TP 3 -  Gestion des paquets

<ol>
<h1>Exercice 1. Commandes de base</h1>

 >`apt full-upgrade`

<li>Quels sont les 5 derniers paquets installés sur votre machine ?</li>


 >`cd /var/log`
 
 >`tail -n 5 dpkg.log`

*affiche les 5 dernière ligne du dpkg.log*

<li>Utiliser dpkg et apt pour compter le nombre de paquets installés (ne pas hésiter à consulter le manuel !).
Comment explique-t-on la (petite) différence de comptage ?
 </li>

  >` dpkg | wc -l ` 

  >` dpkg -l |greep "^ii| wc -l  -> 2234 ligne` 

   >`cd /var/log/apt`

  >` apt list --installed | wc -l -> 2238 ligne ` 

 >` apt list | wc -l `
 
 *dpkgne peut fournir que des informations sur ce qu'il sait, ce qui est limité aux packages et aux versions auxquels une dpkgopération a été appliquée.apt, d’autre part, contient beaucoup plus d’informations - il inclut tout ce qui est contenu dans les listes de paquets qu’il reçoit des dépôts. De toute évidence, il est peu probable que des dpkgopérations aient été effectuées pour la plupart des packages et des versions disponibles, et bien entendu, le résultat de dpkg-queryn'inclut pas ceux-ci et est donc limité.*

 <li>Combien de paquets sont disponibles en téléchargement ?</li>


  >` apt list   | pipe wc-l`

  <li>Créer un alias “maj” qui met à jour le système</li>


   >`vi ./bashrec`
   >`allias maj = apt full-update`
   
   <li>A quoi sert le paquet fortunes ? Installez-le.</li>

  >`sudo apt show  fortunes.`
  >`sudo apt-get install fortune.`

   *Le programme fortune, disponible sous GNU/Linux mais qui provient à l'origine du monde BSD, permet d'afficher aléatoirement des citations*

   <li>Quels paquets proposent de jouer au sudoku ?</li>

   >`sudo apt show  sudoku.`
   >`sudo apt-get install gnome-sudoku`

   <li>Lister les derniers paquets installés explicitement avec la commande apt install</li>

  >`grep apt install /var/log/dpkg.log`

</ol>
<ol>
<h1>Exercice 2.</h1>
<li>A partir de quel paquet est installée la commande ls ? Comment obtenir cette information en une seule
commande, pour n’importe quel programme (indice : la réponse est dans le poly de cours 2, dans la liste des
commandes utiles) ? Utilisez la réponse à pour écrire un script appelé origine-commande (sans l’extension
.sh) prenant en argument le nom d’une commande, et indiquant quel paquet l’a instal</li>


   >`wich -a ls |tail-l|xargs dpkg -s`
   */var/bin/ls ou /bin/ls* 
   >`wich -a ls |xargs dpkg -s 2>/dev/null`

   >`ls | grep doc`

>`touch origine-commande`
>`nano origine-commande`


>`echo $(which -a $1 | xargs dpkg -S 2> /dev/null)`


</ol>

<ol>
<h1>Exercice 3</h1>
<li>Ecrire une commande qui affiche “INSTALLÉ” ou “NON INSTALLÉ” selon le nom et le statut du package
spécifié dans cette commande.</li>

>`touch origine-inst`
>`nano origine-inst`

>`(dpkg -l "$1" |grep"^ii")&&echo"installé || echo"non installé"`

>`chmod u+x origine-inst`
>`./origine-inst *fortune*`

</ol>
<ol>
<h1>Exercice 4</h1>
<li>
Lister les programmes livrés avec coreutils. A quoi sert la commande ’[’ et comment afficher ce qu’elle
retourne ?
</li>

>`apt show coreutils`

*il contient les utilitaires de base pour la manipulatiion de fichier ou de tewte et les scxripts d'interpréteur de commandes qui sont attendus sur tout le systéme*

*la commande crochet évite d'écrire du text pour un bouche ex if test 2>3 == if [2>3]*

<h1>Exercice 5</h1>
<li>
Installez le paquet emacs à l’aide de la version graphique d’aptitude
</li>

>`sudo apt install aptitude `

* on recherche emacs et on l 'install emacs g ++ install in aptitude*
</ol>
