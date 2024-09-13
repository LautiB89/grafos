# Clase resolviendo ejercicios

## Ej 1

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
