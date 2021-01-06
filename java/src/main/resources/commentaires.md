# Commentaires

## Bugs

### 1. Crash du jeu au d�marrage
En essayant de faire tourner le jeu avec plus de 6 joueurs, celui ci plantera du fait de l'initialisation en dur de la taille des array purses et places.
Solution possible: 
	- (quick and dirty) Ajouter une fonction d'initialisation du jeu dans la classe Game, demandant le nombre de joueurs.
	- (un peu mieux) Cr�er une classe joueur, qui contiendra les informations d'un joueur. Les arrays pourront �tre supprim�es du jeu, et la liste des joueurs aujourd'hui en String pourra �voluer vers une liste de Joueur qui connaissent chacun leur �tat.
	
	
### 2. Il manque une protection contre le d�part du jeu si le nombre de joueur est strictement inf�rieur � 2
IndexOutOfBound dans la m�thode roll	

### 3. On ne devrait pas pouvoir faire un 6 avec le d� ?
random.nextInt(6) + 1 (le nextInt exclu la borne fournie donc entre [0 et 5] + 1 -> 1 et 6 )


## Refactoring

### nextPlayer 
Il manque une m�thode 'nextPlayer()' ou quelque chose comme �a, pour encapsuler la m�canique permettant de passer d'un joueur � l'autre.
 
### cases
Une map pour les 'places' rendrait plus lisible et faciliterait les �volutions du plateau de jeu. En utilisant player.currentPlace pour aller chercher dans une map <Integer, Place> par exemple, on ouvre la possibilit� aux �volutions de la complexit� des cases par la suite (pi�ges, bonus etc)

### purses
Serait stock� en tant qu'information du joueur dans la classe Joueur. Sinon en tant que Map pour �viter de se tromper d'index ou d'avoir des soucis d' "outOfBound".


### gameLoop
Pas ma sp�cialit� les jeux, mais je s�parerai bien la "gameLoop" du fonctionnement du jeu. La loop donnerait les ordres au jeu, qui lui ne contiendrait que les r�gles d'un tour pour un joueur. Par exemple, la loop indiquerait � qui est le tour, v�rifierait si un joueur � gagn�, etc.


## Tests
Pas eu le temps de finir �a. Je ne connais pas Approvals.