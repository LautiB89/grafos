# Mi resumen de la materia

## Definiciones rapidas

### Familias de Grafos

- Bosques: grafos que no contienen circuitos.
- Arboles: clase particular de bosques, donde además son conexos.
- Grafos bipartitos?.
- $C_n$: ciclo de n vertices.
- $K_n$: completo de n vertices.
- $K_{n, m}$: bipartito con una biparticion de n vertices y otra de m.
- $P_n$: camino de n vertices.
- $W_n$ (wheel): rueda de n vertices. Se define como un $C_{n-1}$ al que se le agrega un vertice *universal*. Un vertice es *universal* cuando esta conectado a todos los demás.
- $P_n$: camino de n vertices.
- hole: $C_n$ con $n \geq 5$.
- anti-hole: complemento de hole.
- $\bar G$: grafo complemento.
- Cuerda: arista entre dos nodos que no son adyacentes en un ciclo.

#### Grafos pequeños e igualdades

- Diamond: $K_4 - \{e\}$ para cualquier e.
- $C_5 = \bar{C_5}$.
- $P_3 = K_1 + K_2$.
- Cuadrado: $C_4$.
- Paw, Claw...
- Gema: $C_4$ más un universal.

### Otras

- *G*-Free: subclase de grafos definida por no poder tener ningun subgrafo inducido igual (isomorfo) a *G*. (i.e. Triangle-Free o $K_3$-Free)
- Grafos Berge: grafo simple que no contiene ningun hole impar y ningun anti-hole impar.
- Co-Berge: su complemento es Berge. Notar que los Co-Berge son Berge pues $\bar{\text{Hole}}$=Anti-hole
- Cordal/Triangulado: no tiene $C_n$s inducidos con $n \geq 4$.
- Planar: se puede dibujar sin cruzar las aristas. Obs: $K_5$ no es planar. Existe una noción de *reducción* (no la vimos) que permite probar que un grafo *no* es planar sii se reduce (con esa noción) a un $K_5$ o un $K_{3,3}$. Una evidencia de un grafo planar es su dibujo. Los arboles son planares.
- Matriz de cliques de un grafo

### Parámetros

- $\omega(G) = n$ tal que $K_n$ es el clique más grande del grafo G.
- $\chi(G)$ (número cromatico) = mínima cantidad de colores tal que dos vertices adyacentes tienen distinto color.
- Propiedad: $\chi(G) \geq \omega(G)$.
- Decimos que un grafo es bueno si cumple $\chi(G) = \omega(G)$
- Grafo perfecto: si todo grafo inducido G es un grafo bueno. Los grafos completos y los grafos Berge son perfectos.

### Hereditarios

Una grafo cumple la propiedad *P* hereditaria si todo subgrafo inducido cumple con esa propiedad.

- $\alpha(G)$ = mayor cantidad de cliques completos maximales disjuntos. ¿Tamaño del conjunto independiente maximo?
- $\tau(G)$ = tamaño del clique transversal más chico.

### Localmente

Un grafo es localmente X si para todo vertice v del grafo, el subgrafo inducido por la vecindad abierta de v cumple con la propiedad X.

### Grafo de Bloque

Un bloque es una componente biconexa maximal. Dos vertices están en un mismo bloque si remover cualquier otro vertice no los desconecta.

### Grafo de invertalos

Dado un conjunto de invertalos {I1, ..., In}, cada intervalo es un v ()

### Propiedades

- Un grafo es bipartito sii no tiene ciclos de longitud impar
- Los arboles no tienen ciclos (por def), en particular no tienen de longitud impar, por lo que todo arbol es un grafo bipartito.

### Propiedad de Helly

Una familia $\{T_i\}_{i \in I}$ de subconjuntos de T satisface la propiedad de Helly si $J \subseteq I$ y $T_i \cap T_j \not= \emptyset$ para todo $i, j \in J$ implica que $\bigcap_{j \in J} T_j \not= \emptyset$

## Definiciones

- Universo asociado: la unión de los conjuntos de una familia.

### Solucion en clase

G no es clique-helly hereditario y no tiene a ningun grafo ocular como subgrafo inducido.

Existe subfamilia intersecante minimal de cliques que no tiene vertices en común (por?).

Es decir, todos tienen intersección dos a dos pero no existe intersección común (entre todos).

Esa subfamilia de cliques tiene que tener al menos 3 cliques. ¡Si tuviera 2 no podría pasar!

## Retomando

- Weakly Cordal: superclase de cordal. No tiene Hole ni Anti-hole de cualquier longitud.
- Propiedad: Si G es cordal entonces es weakly cordal (duh).

- Strongly Cordal: subclase de cordal. Todo ciclo par de longitud $\geq$ 6 tiene una cuerda de longitud impar.

## Tipos de problemas

- Reconocimiento: responder si un grafo pertenece a una subclase o no. Para haber certificados para el si y el no.
- Isomorfismo: decidir si dos grafos son isomorfos. Dar una f biyectiva de v y de aristas. No hay condiciones suficientes pero si necesarias.
- CIM: conjunto de vertices que no comparten aristas.
- Coloreo: se particionan los vertices en conjuntos independientes. Usar menor cantidad de colores indica un conjunto más grande.
- Grafo linea: se nota $GL(G)$. Se construye creando un vertice por cada arista de G y conectandolos entre ellos solo si las aristas originales compartian alguna punta.
- $\Chi'(G)$ (indice cromatico) = $\Chi(GL(G))$. Es lo mismo que el numero cromatico pero aplicado a aristas.
- Propiedad: $\Delta(G)\geq\Chi'(G)\geq\Delta(G)+1$ ($\Delta$ es el grado máximo de G).
- Clique cover
- Completo maximo

## Tipos de dominancia

...

## Demos

Un grafo ocular es FIXME.

Vamos a probarlo por Contrarrecíproca

- ($\Rightarrow$)

Los grafos oculares no son clique helly (CH) (ver pirámide). Luego, un grafo que los contenga no será clique helly hereditario.

- ($\Leftarrow$)

Sup que G es min no CH y no tiene que grafos oculares. Existe una subfamilia intersecante minimal de cliques que no tienen vértices en comun. La subfamilia intersecante minimal tiene que tener al menos 3 cliques ya que si no habría vertices en común (por ser intersecante).

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
