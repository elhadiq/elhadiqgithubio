# Arbres binaires

### Définition formelle d’un arbre binaire

On appelle arité d’un nœud le nombre de branches qui en partent 3 . Dans la suite de notre cours, nous nous intéresserons plus particulièrement aux arbres binaires, c’est à dire ceux dont chaque nœud a au plus deux fils.</br>
Pour ne pas avoir à distinguer les nœuds suivant leur arité, il est pratique d’ajouter à l’ensemble des arbres binaires un arbre particulier appelé l’arbre vide. Ceci conduit à adopter la définition qui suit.

<div class="alert alert-success" >
     Un ensemble E étant donné, on définit par induction les arbres binaires étiquetés par E en convenant que :
<ul>
<li> [  ] : est un arbre binaire sur E appelé l’arbre vide ;
<li> si x ∈ E et si Fg et Fd sont deux arbres binaires étiquetés par E, alors A = [x,Fg , Fd ] est un arbre binaire étiqueté par E.
</ul>
</div>

x est l’étiquette de la racine de A ; quant à Fg et Fd , ils sont appelés respectivement le sous-arbre gauche et le sous-arbre droit de l’arbre binaire A.<br>
De manière usuelle, on convient de ne pas faire figurer l’arbre vide dans les représentations graphiques des arbres binaires (voir la figure 2). Ainsi, suivant la représentation choisie les feuilles pourront désigner exclusivement l’arbre vide (et dans ce cas tous les nœuds seront d’arité égale à 2) ou alors les nœuds dont les deux fils sont vides (dans ce cas l’arité d’un nœud pourra être égale à 0, 1 ou 2). C’est cette seconde convention qui sera utilisée dans la suite de ce cours.

**Définition.** — La taille |A| d’un arbre A est définie inductivement par les relations :
- |[  ]| = 0 ;
- Si A = (Fg , x, Fd ) alors |A| = 1 + |Fg | + |Fd |.
La hauteur: h(A) d’un arbre A se définit inductivement par les relations :
- h(nil) = −1 ;
- Si A = (Fg , x, Fd ) alors h(A) = 1 + max(h(Fg ), h(Fd )).

Avec ces conventions, |A| est le nombre de nœuds d’un arbre et h(A) la longueur maximale du chemin reliant la racine à une feuille, autrement dit la profondeur maximale d’un nœud.<br>
La définition Python de ces fonctions est immédiate :


```python
taille=lambda A: 0 if A==[] else 1+taille(A[1])+taille(A[2]) 
hauteur=lambda A: 0 if A==[] else 1+max(hauteur(A[1]),hauteur(A[2]))
```


```python
def fiboT(n):
    if n<=1:
        return [n,[],[]]
    G,D=fiboT(n-1),fiboT(n-2)
    return [G[0]+D[0],G,D]
F5=fibo_indexes(5);print(F5)   
```

    [5, [4, [3, [2, [1, [], []], [0, [], []]], [1, [], []]], [2, [1, [], []], [0, [], []]]], [3, [2, [1, [], []], [0, [], []]], [1, [], []]]]
    



```python
print("La taille de F(4) est {}, et son hauteur est {}".format(taille(F4),hauteur(F4)))
```

    La taille de F(4) est 9, et son hauteur est 4
    


<div class="alert alert-success" role="alert">
  This is a success alert—check it out!
</div>
<div class="alert alert-danger" role="alert">
  This is a danger alert—check it out!
</div>
<div class="alert alert-warning" role="alert">
  This is a warning alert—check it out!
</div>
<div class="alert alert-info" role="alert">
  This is a info alert—check it out!
</div>


```python

```
