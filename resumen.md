# Apunte de la materia

## Propiedad de Helly

Una familia $\{T_i\}_{i \in I}$ de subconjuntos de T satisface la propiedad de Helly si $J \subseteq I$ y $T_i \cap T_j \not= \emptyset$ para todo $i, j \in J$ implica que $\bigcap_{j \in J} T_j \not= \emptyset$

## Definiciones

- Universo asociado: la unión de los conjuntos de una familia.

## Retomando

- Weakly Cordal: superclase de cordal. No tiene Hole ni Anti-hole de cualquier longitud.
- Propiedad: Si G es cordal entonces es weakly cordal.
- Strongly Cordal: subclase de cordal. Todo ciclo par de longitud $\geq$ 6 tiene una cuerda de longitud impar.

### Aparte

- Grafo linea: se nota $GL(G)$. Se construye creando un vertice por cada arista de G y conectandolos entre ellos solo si las aristas originales compartian alguna punta.
- $\Chi'(G)$ (índice cromatico) = $\Chi(GL(G))$. Es lo mismo que el numero cromatico pero aplicado a aristas.
- Propiedad: $\Delta(G)\geq\Chi'(G)\geq\Delta(G)+1$ ($\Delta$ es el grado máximo de G).

## Notas de 10-09

### Intro a Set-Packing

Dado el grafo H tq $\alpha(H) \geq k$ queremos encontrar un G tq $\alpha(G^2)\geq k+1$ (es un sii).

Construccion de G: por cada arista de H (v, w) agrego un vertice en el medio llamado vw que está entre ambas, de forma que ahora estan a distancia 2. Todos estos vertices del estilo vw an a conectarse a un vertice llamado x (nuevo) y x además esta conectado a un vertice nuevo llamado z, en resumen:

- Agrego x y z, adyacentes.
- Agrego el vertice vw por cada arista (v, w). Con vw adyacente a x.

De esta forma el grafo nuevo tiene n+m+2 vertices y 3m+1. (se construye con costo polinomial).

Queremos probar que $\alpha(G^2)\geq k$ es NP-Completo. Probar NP es sencillo, ahora vemos que es NP-Hard.

- ($\Rightarrow$)

Existe un conjunto independiente en H de tamaño por lo menos k. Al ser vertices originales de H, sabemos que está en el grafo G por construcción. Además no son adyacentes (por ser conj indep).

Si lo construimos desde un H bipartito, se puede ver que los vertices vw nunca van a estar en la partición de los vertices originales. Entonces x va a estar en la particion de los originales y z en la de los vw. Esto ayuda a ver que si tengo dos vertices que son adyacentes en H, entonces en G van a estar a distancia por lo menos 4.

Al tener z conectado a x, se puede ver que entonces G tiene un conjunto independiente de tamaño k+1 (k del conj indep de H y uno mas por z)

- ($\Leftarrow$)

Suponemos que tenemos la solucion con al menos k+1 vertices, el clique que se genera en G²...

Que pasa si G es bipartito? Sigue siendo NP-Completo.

Que pasa si G es split? Veamos.

Un grafo split es un grafo con dos particiones, donde una es un grafo completo y el otro es un conjunto independiente.

A chequear: Vamos a identificar al grafo split G por su completo K y su conjunto independiente S. Ver que un los unicos cliques posibles en G son de k elementos o de k+1, con k=|K| (dependiendo de si existe algun vertice en S que esté conectado con todos de K o no).

- Si K es clique (osea, es maximal) entonces no puede existir ningun vertice en S cuya vecindad abierta sea K (que esté conectado a todos). Podría existir un vertice en K que no sea adyacente a ninguno en S. Acá tenemos $|S|+1$ cliques
  - Si existe tal vertice: puedo extender a S agregandolo y me queda $\alpha(G)=|S|+1$.
  - Si no existe (S es conjunto independiente maximal) entonces $\alpha(G)=|S|$.
- Si K no es clique, no es maximal porque es completo por definicion. Va a pasar que existe un vertice en S cuya vecindad abierta es K. Entonces su vecindad cerrada es un clique. Entonces...$\alpha(G)=|S|$. ¿Cuantos cliques tengo? Creo que |S|+1
  Notar que la vecindad cerrada de todo vertice en S induce un completo.

### Set packing

Dado un universo U y una familia de subconjuntos F, un packing es una familia C de subconjuntos contenida en F tal que todos los elementos en C son disjuntos dos a dos.

Representacion en grafo: el universo U debería ser completo (K) y la familia de subconjuntos F (S) un conjunto independiente.

Sabiendo que Set-Packing es NP-Completo y viendo que se puede transformar a un grafo split (falta explicar un poco más), podemos concluir que el problema de $\alpha(G) \geq k$ es NP-Completo.

... me perdi un poquito

### Equivalencias

- Set cover en una familia F de subconjuntos y dominacion de vertices para un grafo split G: ver de construir el grafo parecido a como hicimos recien, donde F=K y U=S.

- Dominacion de vertices para grafo split G1 y clique-transversal para grafo split G2: ...

### Teorema

Con un K3 y un C6 vemos que

- Clique Helly:
- Closed Neighborhood Helly: C4, C5, C6 y Piramide.
- Open Neighborhood Helly

Sea $v* \in \bigcap F'$, construyo $F'' = F' \cup \{N(v*)\}_{v* \in \bigcap F'}$ tambien es intersecante. Pero no puede tener intersección etc etc entonces $\bigcap F'' = \emptyset$. Esto demuestra que?

### 17 septiembre

Probó los primeros dos items de la equivalencia:

1. G es closed neighborhood-helly hereditario.
2. G no tiene como subgrafos inducidos a $C_4, C_5, C_6$ ni 3-sun.

Después probó esto:

1. G es open neighborhood-helly hereditario.
2. G no tiene como subgrafos inducicdos a $C_6$ ni triangulo.

- G open neighborhood helly no puede contener triangulo
- Para que no contenga $C_6$ necesitamos pedir que sea open neighborhood helly hereditario.
Supongamos que tiene triangulo

#### clique helly

Dada una familia de subconjuntos, podemos responder (de forma polinomial?) si es clique helly.
Pero el problema esta en que solemos responder la pregunta de si o no para un grafo, no la familia. Si mostramos el tamaño de esta familia en funcion de los tamaños del grafo, vemos que es exponencial, por lo que arranca complicado.

Veamos para el caso especial de los grafos oculares, vamos a encontrar un algoritmo en $O(n^2)$.

Va a ser parecido al algoritmo de Berde.
Definimos una extension:
$$
E(v, w, z) = N[v, w] \cup N[w, z] \cup N[v, z] \text{ si los 3 son}\not=\emptyset \\
E(v, w, z) = \emptyset \text{ si no}
$$

Vamos a probar la siguiente equivalencia:

1. G es un grafo clique helly
2. Para cada extensión $E(v, w, z)$ donde v, w, z inducen un triangulo de G, existe $u \in V$ tal que $E(v, w, z) \subseteq N[u]$.
3. (Esto mejora la complejidad con respecto a 2.)

TOmo 3 elementos del univers
Consigo todos los cliques que tienen al menos 2 de esos 3.
Si algun par de vertices de estos 3 no tiene arista, solo quedan como opcion los otros 2 pares (ya que ese par no podría estar en un clique).
