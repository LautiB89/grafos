# Ejercicios

1. Si un grafo **no** contiene al diamante entonces la intersección de 2 subcliques cualesquiera distintos tiene a lo sumo un solo vertice.
2. ¿CLAW-Free es equivalente a localmente $\bar{K_3}$-Free?
3. ¿Todo grafo es el grafo intersección de alguna familia?
4. idem para grafo containment

Demo que el algoritmo de Berge es correcto:
Si un grafo es de Helly entonces el algoritmo da verdadero.

## Complejidad

Sea el tamaño del universo: $m=|U|$

1. Cuando itero por cada subconjunto de 3 elementos hay ${m\choose3} ≃ m^3$.
   1. Generar $F_T$ requiere recorrer cada $S_i$ y el total de los elementos para hacer la intersección. Cuesta $O(3n)$.
   2. Calcular $\bigcap_{S_i \in F'}S_i$ cuesta $O(mn)$.

### MCL MOMENTO

- D: un duo de elementos a y b
- $F_D$: todos los subconjuntos de $F$ que contiene al duo
- U(D): la intersección de todos los conjuntos en $F_D$.
- T: un trio de elementos a, b y c. Ver que esto tiene 3 duos.
- $?? = U(D_1) \cap U(D_2) \cap U(D_3)$
  La idea de esta ultima intersección es chequearla en vez de chequear el $F_T$ en el paso 3 del algoritmo. La idea es tomar los 3 elementos, generar los 3 duos posibles (ab, ac, bc) y generarar $U(D_i)$ con cada uno para hacer la intersección final.
  Lo que el afirma es que es lo mismo chequear, es un sii la condicion del $F_t = \emptyset$ y $?? = \emptyset$

1. m² de ver todos los posibles duos
2. ...
