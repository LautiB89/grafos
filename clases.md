# Apunte de Clases/Subclases/Familias de grafos

## Familias de Grafos

- Bosques: grafos que no contienen circuitos.
- Arboles: clase particular de bosques, donde además son conexos.
- Grafos bipartitos: se puede separar en dos conjuntos (particiones) de forma que todas las aristas del grafo conectan vertices de distinas particiones.
- $C_n$: ciclo de n vertices.
- $K_n$: completo de n vertices.
- $K_{n, m}$ bipartito completo: bipartito con una biparticion de n vertices y otra de m, donde se dan todas las aristas posibles en el bipartito.
- $P_n$: camino de n vertices.
- $W_n$ (wheel): rueda de n vertices. Se define como un $C_{n-1}$ al que se le agrega un vertice _universal_. Un vertice es _universal_ cuando esta conectado a todos los demás.
- $P_n$: camino de n vertices.
- hole: $C_n$ con $n \geq 5$.
- anti-hole: complemento de hole.
- $\bar G$: grafo complemento.
- Cuerda: arista entre dos nodos que no son adyacentes en un ciclo.

### Grafos pequeños e igualdades

- Diamond: $K_4 - \{e\}$ para cualquier e.
- $C_5 = \bar{C_5}$.
- $P_3 = K_1 + K_2$.
- Cuadrado: $C_4$.
- Paw: $K_3$ con un vertice agregado adyacente a un vertice del completo.
- Claw (otro nombre para el $K_{1,3}$). Se construye tomando $\overline{K_3}$ y agregandole un vertice universal.
- Gema: $C_4$ más un universal.

## Otras

- _G_-Free: subclase de grafos definida por no poder tener ningun subgrafo inducido igual (isomorfo) a _G_. (i.e. Triangle-Free o $K_3$-Free)
- Grafos Berge: grafo simple que no contiene ningun hole impar y ningun anti-hole impar.
- Co-Berge: su complemento es Berge. Notar que los Co-Berge son Berge pues $\bar{\text{Hole}}$=Anti-hole
- Cordal/Triangulado: no tiene $C_n$s inducidos con $n \geq 4$.

## Grafos planares

- Planar: se puede dibujar sin cruzar las aristas. Obs: $K_5$ no es planar. Existe una noción de _reducción_ (no la vimos) que permite probar que un grafo _no_ es planar sii se reduce (con esa noción) a un $K_5$ o un $K_{3,3}$. Una evidencia de un grafo planar es su dibujo. Los arboles son planares.

### Teorema de Kurtowski

Un grafo es planar sii no contiene un subgrafo que es subdivisión elemental de $K_5$ o $K_{3,3}$. Una subdivision elemental es tomar una arista (v, w) y dividirla en dos agregando un vertice nuevo: (v, z) y (z, w). La operacion inversa se llama suavizado/alisado.

## Parámetros

- Clique number: $\omega(G) = n$ tal que $K_n$ es el clique más grande del grafo G.
- $\chi(G)$ (número cromatico) = mínima cantidad de colores tal que dos vertices adyacentes tienen distinto color.
- Propiedad: $\chi(G) \geq \omega(G)$. Si G contiene un clique de tamaño k, entonces se necesitan al menos k colores para colorear ese clique.
- Decimos que un grafo es bueno si cumple $\chi(G) = \omega(G)$
- Grafo perfecto: si todo grafo inducido G es un grafo bueno. Los grafos completos y los grafos Berge son perfectos.

## Clases hereditarias

Una propiedad es hereditaria cuando los subgrafos inducidos del grafo que la cumple tambien la cumplen (la heredan). Es equivalente a pedir que se preserve la propiedad al eliminar vertices.

Una clase de grafos es hereditaria si esta cerrada por sus subgrafos inducidos.

- $\alpha(G)$ = Tamaño del conjunto independiente maximo. Se lo puede llamar numero de independencia ¿mayor cantidad de cliques completos maximales disjuntos?.
- $\tau(G)$ = tamaño del clique transversal más chico.

## Localidad

Un grafo es localmente X si para todo vertice v del grafo, el subgrafo inducido por la vecindad abierta de v cumple con la propiedad X. Algunas clases del estilo son:

- Localmente completo
- Localmente independiente
- Claw-Free es equivalente a localmente Co Triangle-Free (lo mismo que $\bar{K_3}$-Free)

## Grafos con una representación o modelo

- Grafos intersección: dada una familia de conjuntos, se puede crear su grafo de intersección asignando un vertice a cada conjunto y conectando dos vertices entre si si sus conjuntos asociados intersecan. Todo grafo G (no dirigido) es un grafo de intersección.
  - FIXME: El intersection number de un grafo es la cantidad minima de elementos necesarios en una representacion de G como un grafo de interseccion sobre conjuntos finitos.
- Grafos overlap: un grafo es si cada vertice se puede asociar a un intervalo en una recta de forma tal que dos vertices son adyacentes sii sus intervalos se superponen parcialmente (tienen intersección no nula y ninguno contiene al otro).
- Grafos containment: un grafo lo es si se puede modelar con objetos tal que dos vertices son adyacentes sii uno de los objetos está contenido en el otro.
- Grafo de comparabilidad: es de comparabilidad si se puede orientar de forma transitiva (si a->b y b->c son aristas entonces a->c tambien).

## Subclases de grafo intersección

- Grafo clique ($K(G)$):
- Grafo biclique ($B(G)$):
- Grafo de línea ($L(G)$): ... Se puede generar en tiempo polinomial.
- Grafo de Bloque: un bloque es una componente biconexa maximal. Dos vertices están en un mismo bloque si remover cualquier otro vertice no los desconecta.
- Grafo de invertalos: dado un conjunto de invertalos $\{I_1, \dots, I_n\}$, cada intervalo es un vertice ($\{v_1, \dots, v_n\}$) y existe la arista $(v_i, v_j) \iff I_i\cap I_j \not= \emptyset$
  - Propio
  - Unitario
- Arco-circulares: grafo de intervalos donde estos se pueden representar con un círculo.
  - Propio
  - Unitario
  - Helly
  - Normal
- Circulares: dado un grafo ciclo con cuerdas, un grafo circular es el formado por la intersección de las cuerdas.
- Permutación: grafos cuyos vértices representan los elementos de una permutación y cuyas aristas representan pares de elementos que quedaorn al revés luego de permutar.
- Trapezoide: grafo que se forma a partir de la intersección de trapezoides entre dos líneas paralelas.

## Otras subclases

### Potencias y raices

- $G^k$: el grafo resultante de conectar los vertices de $G$ que estén a distancia $\leq k$.
- $\sqrt[k]{G}$: es la operacion inversa de $G^k$.

### Particiones

- Grafo bipartito
- Grafo split
- Grafo polar

### Ordenes de eliminación

- Grafos cordales:
  - Weakly Cordal: superclase de cordal. No tiene Hole ni Anti-hole de cualquier longitud.
  - Propiedad: Si G es cordal entonces es weakly cordal.
  - Strongly Cordal: subclase de cordal. Todo ciclo par de longitud $\geq$ 6 tiene una cuerda de longitud impar.
- Grafos dualmente cordales
- Grafo de eliminación
- Grafo balanceado

## Propiedades

- Un grafo es bipartito sii no tiene ciclos de longitud impar
- Los arboles no tienen ciclos (por def), en particular no tienen de longitud impar, por lo que todo arbol es un grafo bipartito.
