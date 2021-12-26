---
title: "Tri"
date: 2021-12-26T03:40:09+01:00
Description: ""
Tags: []
Categories: []
DisableComments: false
---
```python
def tri_bulle(T):
    ##Intératif
    n=len(T)
    if n<=1:
        return T
    for i in range(n):
        for j in range(n-1,0,-1):
            if T[j]<T[j-1]:
                 T[j],T[j-1]= T[j-1],T[j]
T=[9,1,2,19,10,11,8,0]
tri_bulle(T)
T
```




    [0, 1, 2, 8, 9, 10, 11, 19]




```python
def tri_Insertion(T):
    n=len(T)
    if n<=1:
        return T
    for j in range(1,n):
        key=T[j]
        i=j
        while i>0 and key<T[i-1]:
            i=i-1
        #Insertion
        if i!=j:
            T[:j+1]=T[:i]+[key]+T[i:j]

T=[9,1,2,19,10,11,8,0]
tri_Insertion(T)
print(T)
```

    [0, 1, 2, 8, 9, 10, 11, 19]



```python
def fusion(sorted1,sorted2):
    i,n1=0,len(sorted1)
    j,n2=0,len(sorted2)
    result,current=[],_
    while (i<n1 and j<n2):
        if (sorted1[i]<sorted2[j]):
            current=sorted1[i]
            i+=1
        else:
            current=sorted2[j]
            j+=1
        result.append(current)
    result.extend(sorted1[i:]+sorted2[j:])
    return result

    
def Tri_fusion(T):
    n=len(T)
    if n<=1:
        return T
    if n==2:
        return T if T[0]<T[1] else [T[1],T[0]]
    return fusion(Tri_fusion(T[:n//2]),Tri_fusion(T[n//2:]))
T=[9,1,2,19,10,11,8,0]
Tri_fusion(T)
```




    [0, 1, 2, 8, 9, 10, 11, 19]



## Quick Sort


```python
def partition(T,p,r):
    if T==[]:
        return -1
    i=p-1
    x=T[r]
    for j in range(p,r):
        if T[j]<=x:
            i+=1
            T[i],T[j]=T[j],T[i]
    T[r],T[i+1]=T[i+1],T[r]
    return i+1
```


```python
T=[2,8,7,1,3,5,6,4]
print(partition(T,1,len(T)-1))
print(T)
```

    3
    [2, 1, 3, 4, 7, 5, 6, 8]



```python
def quick_sort(T,p=None,r=None):
    if T==[]:
        return None
    if p is None:
        p=0
    if r is None:
        r=len(T)-1
    if p<r:
        d=partition(T,p,r)
        quick_sort(T,d+1,r)
        quick_sort(T,p,d-1)
```


```python
T=[2,8,7,1,3,5,6,4]
quick_sort(T)
```


```python
T
```




    [1, 2, 3, 4, 5, 6, 7, 8]




```python
from random import randint
```


```python
def randomise_partition(T,p,r):
    if T==[]:
        return -1
    i=randint(p,r)
    T[i],T[r]=T[r],T[i]
    return partition(T,p,r)
```


```python
def quick_sort_randomise(T,p=None,r=None):
    if T==[]:
        return None
    if p is None:
        p=0
    if r is None:
        r=len(T)-1
    if p<r:
        d=randomise_partition(T,p,r)
        quick_sort_randomise(T,d+1,r)
        quick_sort_randomise(T,p,d-1)
```


```python
T=[2,8,7,1,3,5,6,4]
quick_sort_randomise(T)
```


```python
T
```




    [1, 2, 3, 4, 5, 6, 7, 8]



# Tri lineaire


```python
A =[5,1, 3, 4, 3, 1, 4, 5, 0,1]
```


```python
def counting_sort(T):
    if T ==[]:
        return None
    k=max(T)+1
    occ=[0]*k
    for i in T:
        occ[i]+=1
    j=0
    for k,o in enumerate(occ):
        for i in range(o):
            T[j]=k
            j+=1
```


```python
counting_sort(A)
```


```python
A
```




    [0, 1, 1, 1, 3, 3, 4, 4, 5, 5]




```python
B=[10,3,2,7,8,8]
counting_sort(B)
B
```




    [2, 3, 7, 8, 8, 10]




```python
def counting_sort2(T):
    n=len(T)
    k=max(T)+1
    occ=[0]*k
    B=[0]*(n+1)
    for t in T:
        occ[t]+=1
    for j in range(1,k):
        occ[j]+=occ[j-1]

    for j in range(n-1,-1,-1):
        B[occ[T[j]]]=T[j]
        occ[T[j]]-=1
    return B[1:]
```


```python
B=[10,3,2,7,8,8]
counting_sort2(B)
```




    [2, 3, 7, 8, 8, 10]




```python
def tri_denombrement( A ):
    n =len(A)
    B =[0]*(n+1)
    k=max(A)+1
    C=[0]*k
    for j in range ( n ):
    C [A[j]]=C[A[j]]+1
    for i in range (1,k):
    C [ i ]= C [ i ] + C [i -1]
    for j in range (n -1 , -1 , -1):
    B [ C [ A [ j ]]]= A[ j ]
    C [ A [ j ]]= C [ A [j ]] -1
    return B [1:]
```


```python
def centree_reduit(T):
    mn,mx=min(T),max(T)
    assert mn<mx
    B=[]
    for v in T:
        B.append((v-mn)/(mx+mn))
    return (B,mn,mx)
```


```python
import numpy as np
```


```python
A=list(np.random.uniform(1,10,size=30))
```


```python
A
```




    [8.86636780729286,
     9.33870242272593,
     5.739519137277574,
     1.5697606576397083,
     7.669055807049516,
     6.189078469771015,
     8.785032826730923,
     4.435467726705012,
     1.7368261876092,
     1.5480039986369736,
     7.672507896272754,
     5.181664658710018,
     5.403146909713819,
     3.5526305994070912,
     9.915669671219646,
     1.3066999776684702,
     9.087202120366568,
     2.2271709786084513,
     9.65769953861588,
     9.128281761962638,
     4.155399445733458,
     6.9505565765266555,
     3.693957098977001,
     5.702897902550942,
     3.7775505553428985,
     1.2601488826457645,
     8.777549432494137,
     1.081983185146442,
     7.266458652190323,
     7.695607738796078]




```python
app=centree_reduit(A)
```


```python
def centree_reduit_inverse(Tab,mn,mx):
    B=[]
    for v in Tab:
        B.append(v*(mx+mn)+mn)
    return B
```


```python
B=centree_reduit_inverse(app[0],app[1],app[2])
```


```python
B
```




    [8.866367807292859,
     9.33870242272593,
     5.739519137277574,
     1.5697606576397083,
     7.669055807049516,
     6.189078469771015,
     8.785032826730923,
     4.435467726705012,
     1.7368261876092,
     1.5480039986369736,
     7.672507896272754,
     5.181664658710018,
     5.403146909713819,
     3.5526305994070917,
     9.915669671219646,
     1.3066999776684702,
     9.087202120366568,
     2.2271709786084513,
     9.65769953861588,
     9.128281761962638,
     4.155399445733458,
     6.950556576526656,
     3.693957098977001,
     5.702897902550942,
     3.7775505553428985,
     1.2601488826457645,
     8.777549432494137,
     1.081983185146442,
     7.266458652190323,
     7.695607738796078]




```python
 
```
