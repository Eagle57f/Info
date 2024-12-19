# Cours d'informatique en ECG1-2

Les parties en _italique_ sont des approfondissements qui pourraient être utiles.

<details>
  <summary style="font-weight: bold">Quelques ressources pour appronfondir <span style="font-style: italic">(cliquez pour afficher)</span></summary>
  
- **Vidéos (ou playlists):**
    - Graven (FR): https://www.youtube.com/watch?v=psaDHhZ0cPs&list=PLMS9Cy4Enq5JmIZtKE5OHJCI3jZfpASbR
    - Docstring (FR): https://www.youtube.com/watch?v=LamjAFnybo0&list=PLXDBYzqsqO3Wut-gQktoqJ30eaOel0hgb
    - FormationVidéo (FR): https://www.youtube.com/watch?v=HWxBtxPBCAc&list=PLrSOXFDHBtfHg8fWBd7sKPxEmahwyVBkC
    - NetworkChuck (EN): https://www.youtube.com/watch?v=mRMmlo_Uqcs
    - freeCodeCamp.org (EN): https://www.youtube.com/watch?v=LHBE6Q9XlzI

- **Sites web:**
    - Python Doctor (FR): https://python.doctor/
    - w3schools (EN): https://www.w3schools.com/
</details>




## TP 1 - Introduction à l'algorithmique, présentation de python et exemples

- **Quelques symboles**
    
    |+|-|*|**|/|//|_%_|
    |:-:|:-:|:-:|:-:|:-:|:-:|:-:|
    |Addition `1+2==3`|Soustraction `1-2==-1`|Multiplication `2*3==6`|Puissance `2**3==8`|Division `6/2==3`|Quotient division euclidienne `7//2==3`|_Reste division eculidienne `7%2==1`_|

    Les chiffres à virgule s'écrivent avec un point en python. Ex: `1.005`
    
- **Variables et affichage**

    Un algorithme python s'exécute dans l'ordre(1ère ligne->dernière ligne), il faut donc initialiser les variables avant de les utiliser.
    ```python
    a="t"
    b,c=2,3 # b==2 et c==3
    print(a,c,b) # print permet d'afficher des valeurs dans le terminal
    ```
    Python est sensible à la casse, donc `Variable != variable`.

- **Premières fonctions**

    |abs()|int()|max()|min()|round()|
    |:-:|:-:|:-:|:-:|:-:|
    |Valeur absolue `abs(-3)==3`|Supprime la partie fractionnaire `int(-3.7)==-3`|Maximum `max(2,3,6)==6`|Minimum `min(2,3,6)==2`|Arrondi à 10^(-n) près `round(3.577,1)==3.6`|

- **Première bibliothèque: math**

    Il faut toujours importer la bibliothèque avant d'utiliser une fonction ou variable de cette bibliothèque. Le plus souvent, il est préférable d'importer les bibliothèques au début du fichier, afin quelles soient disponibles dans tout le fichier.
    
    Pour importer la bibliothèque math:
    ```python
    import math
    print(math.pi)
    # OU
    from math import *
    print(pi)
    ```

    |math.pi|math.floor(x)|math.sqrt(x)|
    |:-:|:-:|:-:|
    |π|⌊x⌋ `math.floor(-3.7)==-4`|√x `math.sqrt(9)==3`|

    `math.pi` n'est pas une fonction mais une variable, il ne faut donc pas écrire `math.pi()` mais `math.pi`.

- **Bibliothèque fractions**
    
    Ne pas écrire `from Fraction import *`, mais `from fractions import *`.

    _**Pour mieux comprendre:** Le nom de la librairie est `fractions` et une classe (un "outil") de cette bibliothèque est `Fraction`. Un import est de la forme `from fichier import outil` ou fichier est le nom de la bibliothèque et outil est le nom de la classe, fonction ou variable qu'on souhaite utiliser._

    ```python
    from fractions import *
    numerateur=3
    denominateur=12
    a=Fraction(numerateur, denominateur)
    print(a.numerator) # Renvoie le dénominateur de la fraction simplifiée
    print(a.denominator) # Renvoie le numérateur de la fraction simplifiée
    print(a) # Renvoie la fraction simplifiée
    b=Fraction(2, 3)
    print(a*b, a/b, a+b, a-b, a//b, a**b) # Renvoie: 1/6 3/8 11/12 -5/12 0 0.3968502629920499  Mêmes opérations que pour les nombres (int, float).
    ```
- **Symboles de tests**
    |==|<|>|!=|<=|>=|
    |:-:|:-:|:-:|:-:|:-:|:-:|
    |Egal|Strict. inf.|Strict. sup.|N'est pas égal|Inf. ou égal|Sup. ou égal|

    Si le test est vrai (Ex: `6==2*3`), alors il renvoie `True`, sinon `False`.

## TP 2 - Boucles for et while, tests
- **Fonction input et eval:**

    La fonction `input()` permet de demander une valeur à l'utilisateur. Cette valeur peux être n'importe quelle chaîne de caractères. La valeur retournée par input sera toujours une chaîne de caractère `str`, même si on entre une valeur comme `34`, `1.8` ou `True`.

    `input` prend 1 argument qui est le texte affiché dans la demande de la valeur (Exemple: `input("Donnez un entier entre 1 et 10: ")`).

    Pour obtenir un `int` lorsque l'utilisateur entre un entier, un `float` lorsque l'utilisateur entre un nombre décimal, ..., il faut utiliser la fonction eval, qui grâce au contexte (donc grâce à la "forme" de la valeur : 2 => int, 1.2 => float, ...), eval va transformer le `str` en un autre type.

    ```python
    print(input("Donne un nombre")) # L'utilisateur entre 2 => le programme affiche "2"
    print(eval(input("Donne un nombre"))) # L'utilisateur entre 3 => le programme affiche 3
    ```

- **Boucles `for`**

    La boucle `for` permet de répéter une action un nombre connu de fois.

    Elle est de la forme:

    ```python
    a=2
    b=7
    c=2
    for i in range(a, b, c):
        print(i) # Il faut indenter les lignes à l'intérieur de la boucle
    ```
    La boucle ci-dessus prends les valeurs entre a et b-1, avec a et b entiers. Si on ajoute la valeur c, on va avancer de c en c entre a et b, donc a, a+c, a+2c, ... jusqu'à ce que a+kc soit supérieur ou égal à b (dans quel cas la boucle s'arrête).

    Par exemple, on peut utiliser cette boucle pour calculer uₙ :

    ```python
    u=2 # Valeur de u₀
    n=10
    for i in range(n): # Lorsqu'on met une seule valeur, la boucle va de 0 à n-1, donc la boucle se lance n fois.
        u=u*3+4
    print(u) # Affiche u₁₀
    ```

    On peut utiliser la valeur i, qui prend les valeurs parcourues par range(a,b,c). Par exemple pour calculer la somme des entiers entre 0 et n:

    ```python
    S=0
    n=10
    for i in range(n+1):
        S=S+i
    print(S)
    ```

    La boucle `for` permet également de calculer la somme ou le produit de termes (qui peuvent être en fonction de i):

    ```python
    s=0 # Pour les sommes de termes, il faut initialiser la variable à 0
    a=2
    b=10
    for i in range(a, b):
        s=s+i+2
    print(s)
    ```

    ```python
    p=1 # Pour les produits de termes, il faut initialiser la variable à 1
    a=2
    b=10
    for i in range(a, b):
        p=p*(i+2)
    print(p)
    ```
    Pour calculer la limite d'une somme ou d'un produit, il suffit de choisir un b très grand.


- **Boucles `while`**

    La boucle `while` est utilisée lorsqu'on veut répeter une action tant qu'une condition n'est pas atteinte.

    Par exemple, pour afficher les entiers entre 0 et n-1:

    ```python
    a=0
    b=5
    while a<b: # Ici, la boucle est répetée jusqu'à ce que a>=b
        print(a)
        a=a+1
    ```

    Grâce à la boucle while, on peut trouver le premier k tel que uₖ est par exemple supérieur à une valeur.

    ```python
    u=0 # La valeur de u₀
    k=0
    while u<20:
        k=k+1
        u=u**2+2
    print(k)
    ```

- **Fonctions de la bibliothèque `math`**

    Il faut importer math avant de les utiliser.

    |math.exp(x)|math.log(x)|math.log2(x)|math.log10(x)|
    |:-:|:-:|:-:|:-:|
    |eˣ `math.exp(0)==1`|ln(x) `math.ln(1)==0`|Logarithme base 2 `math.log2(8)==3`|Logarithme base 10 `math.log10(10)==2`|

- **Tests**

    ```python
    a=eval(input("Donnez un chiffre appartenant à Z: "))
    if a==0:
        print("a est égal à 0")
    elif a>0:
        print("a est supérieur à 0")
    else:
        print("a est inférieur à 0")
    ```

- **Fonction de la bibliothèque random**
    ```python
    import random
    print(random.random()) # Renvoie un float entre O inclu et 1 exclu
    print(random.random()*10) # Renvoie un float entre 0 inclu et 10 exclu
    print(random.random()*10+4) # Renvoie un float entre 4 inclu et 14 exclu
    print(int(random.random()*10+5)) # Renvoie un int entre 4 inclu et 14 inclu

    # Hors programme pour le TD1 et 2:
    print(random.randint(4,14)) # Renvoie un int entre 4 inclu et 14 inclu
    ```

- **Algorithme de conversion en binaire (base 2)**

    ```python
    n = eval(input("Donnez un nombre entier naturel: "))
    nbin = ""
    if n == 0:
        nbin = "0"
    else:
        while n > 0:
            nbin = str(n%2) + nbin # Il faut ajouter les valeurs à gauche
            n //= 2
    print(nbin)
    ```
- **Algorithme de dichotomie (version sans fonctions)**

    Qu'il faudra soit apprendre par coeur, soit savoir retrouver rapidement.

    ```python
    p=eval(input("Précision: "))
    a=eval(input("Valeur de a: "))
    b=eval(input("Valeur de b: "))
    while abs(b-a)>p:
        m=(a+b)/2
        if (a**3+3*a-5)*(m**3+3*m-5)<0:
            b=m
        else:
            a=m
    print([a,m,b]) # x est compris entre a et b, et (a+b)/2 est le milieu de cet intervalle, donc la meilleure approximation
    ```

- **Algorithme de dichotomie (version avec fonctions)**

    ```python
    def d(a,b,f,p): # a et b deux réels entre lesquels il faut trouver alpha tel que f(alpha)=0, f la fonction et p la précision (par exemple 0.001)
        while abs(b-a)>p:
            if f(a)*f((a+b)/2)<0:
                b=(a+b)/2
            else:
                a=(a+b)/2
        return [a,(a+b)/2,b] # x est compris entre a et b, et (a+b)/2 est le milieu de cet intervalle, donc la meilleure approximation
    def f(x): return x**3+3*x-5 # Mettre ici la fonction qu'il faut étudier, par exemple x**3+3*x-5
    print(d(10,1,f,0.0001))
    ```
