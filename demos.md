# Clase resolviendo ejercicios

1. Probar que los grafos clique-Helly hereditarios son exactamente los grafos que no tienen como subgrafos inducidos a los grafos oculares (3-sun,$\overline{3K_2}$,$\overline{P_4 + P_2}$,$\overline{E}$)
2. Probar que los grafos containment son exactamente los grafos de comparabilidad (admiten una orientacion transitiva de sus aristas)
3. Probar que son equivalentes las siguientes subclases de grafos.
   1. localmente completo
   2. $P_3$-free
   3. union de cliques/completos
4. Probar que los grafos localmente independiente son exactamente los grafos sin triangulos
5. Probar que un grafo es localmente co-triangle-free sii es claw-free
6. Probar que cualquier grafo es grafo interseccion y grafo overlap
7. Mostrar un grafo que no es containment/de comparabilidad
8. Probar que los grafos cordales son weakly chordal
9. Probar que los grafos de bloques (grafos interseccion de los bloques de grafos) son exactamentes los grafos donde todos sus bloques son completos.
10. Probar que los grafos de permutacion son de comparabilidad y de co-comparabilidad (la vuelta tambien es cierta).
11. Probar que los grafos split son cordales y co-cordales (vale la vuelta tambien).
12. Probar que los grafos de intervalos son cordales y de co-comparabilidad (la vuelta tambien se cumple).
13. Probar que cualquier grafo es grafo interseccion de una familia donde cada miembro es la union de uno o varios intervalos de una lınea recta.

## Ej1

### Consigna

Probar que los grafos clique-Helly hereditarios son exactamente los grafos que no tienen como subgrafos inducidos a los grafos oculares $(3-sun, \overline{3K_2}, \overline{P_4 + P_2}, \overline{E})$.

### Recordatorio

- 3-sun: es un $K_3$ con 3 rayos de sol (la trifuerza de zelda).

```txt
 ▲
▲ ▲
```

- $\overline{3K_2}$ es el 3-sun agregandole orejitas, conectan las puntas externas del triangulo.
- $\overline{P_4 + P_2}$ es el 3-sun con una oreja faltante, solo tiene 2.
- $\overline{E}$: $E$ es el grafo que se genera haciendo la letra. Al complementarlo nos da el 3-sun agregando solo una oreja.

Basicamente, estos ultimos 3 grafos son agregarle 1, 2 y 3 orejas al 3-sun.

#### Extra: Sun Graph

En realidad los sun graph (tmb conocido como trampoline graph) se definen para cualquier n: es un grafo de 2n nodos construido con un grafo central completo $K_n$ con un anillo externo de n vertices, donde cada uno se conecta a las dos puntas de la arista externa mas cercada del grafo central. (FIXME, está raro).

Otra definicion es: A sun is a chordal graph on 2n nodes $(n \geq 3)$ whose vertex set can be partitioned into $W = \{w_1 \dots w_n\}$ and $U = \{u_1\dots u_n\}$ such that $W$ is independent and $u_i$ is adjacent to $w_j \iff i=j$ or $i=j+1$ (mod n). Example: $S_3 ,S_4$.

### Solución

### Ida

Primero ver que cada uno de los grafos oculares no es clique-Helly. Si es cierto entonces cualquier grafo clique-Helly hereditario no puede contener a estos grafos como subgrafos inducidos

#### Verificar que los oculares no son clique-helly

Para esto, por cada uno de los grafos, buscamos una subfamilia de la familia de cliques y mostramos que la intersección del conjunto de sus vertices es nula. Tomando el 3-sun, vemos que contiene 3 cliques (c/u de los triangulos). Se ve que intersecar cualquier par de cliques de estos 3 nos va a dar el vertice que comparten, pero intersecar los 3 cliques a la vez nos va a dar vacío. Con esto alcanza para ver que 3-sun no es clique-helly.

Ver que los otros 3 oculares tienen al 3-sun inducido y los mismos 3 cliques que usamos siguen siendo cliques en los oculares (las orejas no cambian su condicion de maximales), por lo que se puede ver que ninguno es clique-helly.

### Vuelta por absurdo

Sea G un grafo lo más chico posible que no contiene a ninguno de los grafos oculares como inducido y no es clique-helly hereditario. Entonces G no es clique-helly.

Sea $F'=\{Q_1, \dots, Q_k\}$ una subfamilia de cliques de G intersecante (siempre hay intersección dos a dos) minimalmente no Helly (intersección de todos es vacía, pero sacar cualquier $Q_i$ la vuelve no vacía). Por su definicion se puede ver que $k\geq 3$ (si no intersecante y minimalmente no Helly estarían en contradicción).

Tomamos las siguientes subfamilias de $F'$.

$$
F'(1) = F'-\{Q_1\} \text{, con a un vertice en común de sus cliques}\\
F'(2) = F'-\{Q_2\} \text{, con b un vertice en común de sus cliques}\\
F'(k) = F'-\{Q_k\} \text{, con c un vertice en común de sus cliques}\\
$$

Es facil observar que:

$$
Q_1 \cap \{a, b, c\} = \{b, c\}\\
Q_2 \cap \{a, b, c\} = \{a, c\}\\
Q_k \cap \{a, b, c\} = \{a, b\}\\
$$

```text
FIXME: este ultimo argumento no me cierra
```

Por otro lado $\{a, b, c\}$ es parte de un clique $Q$ y $Q \not= Q_i$ para $i \in \{1, 2, k\}$. Por lo tanto, existen otros 3 vértices distintos $v_1, v_2, v_k$ tal que:

- $v_1 \in Q_1$ no adyacente a $a$
- $v_2 \in Q_2$ no adyacente a $b$
- $v_k \in Q_k$ no adyacente a $c$

Claramente, el grafo $G[\{a, b, c, v_1, v_2, v_k\}]$ es ocular y eso es una contradicción.

## Ej2

### Consigna

Probar que los grafos containment son exactamente los grafos de comparabilidad (admiten una orientación transitiva de sus aristas).

### Recordatorios

- Grafos containment: un grafo lo es si se puede modelar con objetos (subconjuntos) tal que dos vertices son adyacentes sii uno de los objetos (subconjuntos) está contenido en el otro.
- Grafo de comparabilidad: es de comparabilidad si se puede orientar de forma transitiva (si a->b y b->c son aristas entonces a->c tambien).

### Solución

#### Ida

Sea G un grafo containment asociado a una familia de subconjuntos $F = \{S_1, \dots, S_n\}$ tal que dos vértices $v_i, v_j$ del grafo son adyacentes sii los subconjuntos correspondientes $S_i, S_j$ verifican $S_i \subseteq S_j$ o $S_j \subseteq S_i$.

Podemos orientar las aristas de G de la siguiente manera: sea $(v_i, v_j)$ una arista de G, entonces queda $v_i \rightarrow v_j$ si $S_i \subseteq S_j$ o $v_j \rightarrow v_i$ si $S_j \subseteq S_i$. Basicamente, la orientacion respeta el sentido de la contención.

Claramente, la orientación resultante es transitiva ya que la relación de contención entre conjuntos también es transitiva.

#### Vuelta

Sea G=(E, V) un grafo de comparabilidad y H una orientación transitiva de sus aristas. Busquemos una familia de conjuntos para la cual G es su grafo de containment.

Para cada vértice $v\in V$, definimos $N^{\text{out}}_H(v)=\{w | v \rightarrow w \in H\} \cup \{v\}$. Ahora consideramos la familia F donde sus miembros son $N^{\text{out}}_H(v)$ para $v\in V$. Veamos que G es grafo containment de F:

- (u, v) es una arista de E y sin perdida de generalidad $u\rightarrow v \in H$ es su orientación. Veamos que $N^{\text{out}}_H(v) \subseteq N^{\text{out}}_H(u)$. Para cada vertice $z \in N^{\text{out}}_H(v)$ consideramos los siguientes subcasos:
  - $z = v$, entonces $z = v \in N^{\text{out}}_H(u)$
  - $z \not= v$ y $v\rightarrow z \in H$. Como H es transitiva entonces $u \rightarrow z \in H$ y $z \in N^{\text{out}}_H(u)$.
Por lo cual, (u, v) es una arista del grafo containment de F.
- (u, v) es una arista del grafo containment de F y sin pérdida de generalidad podemos suponer que $N^{\text{out}}_H(v) \subseteq N^{\text{out}}_H(u)$. Por lo cual, $u \rightarrow v \in H$ y (u, v) es una arista de E.

## Ej3

### Consigna

Probar que son equivalentes las siguientes subclases de grafos:

- Localmente completo
- $P_3$-Free
- unión de cliques/completos

## Ej4

### Consigna

Probar que los grafos localmente independientes son exactamente los grafos sin triángulos

## Ej5

### Consigna

Probar que un grafo es localmente co-triangle-free sii es claw-free
