# 5. Requêtes simples

* Afficher un tableau d'appairage entre noms d'acteurs et titres de films

![image](https://user-images.githubusercontent.com/73080397/226095572-fe202757-6694-4ae6-9ab5-87f69cad2078.png)

A votre tour, écrire des requêtes pour afficher :

* La valeur de la propriété title pour tous les nœuds ayant cette propriété
```cypher
MATCH (node) RETURN node.title
```

* Les nœuds connectés par une relation ACTED_IN, le résultat doit ressembler à:

![image](https://user-images.githubusercontent.com/73080397/226097604-4ccaa949-fd36-43b5-a3b0-20faee58aee0.png)

```cypher
MATCH (node1)-[:ACTED_IN]->(node2) RETURN node1, node2
```

* Les personnes et les films dans lequels ils ont participé, le résultat doit ressembler à :

![image](https://user-images.githubusercontent.com/73080397/226097813-1d71a287-b205-45c0-a10e-cfe29bf3b9d5.png)

* Les acteurs et leurs rôles (personnages) dans le film « The Matrix »

```cypher
MATCH (actor:Person)-[role:ACTED_IN]->(movie:Movie) WHERE movie.title="The Matrix" RETURN actor.name, role.roles
```

* Les films dans lesquels TOM Hanks a joué, le résultat doit rassembler à :

![image](https://user-images.githubusercontent.com/73080397/226098001-9f3611f3-a6b8-45b2-a75e-17606ba4080a.png)

```cypher
MATCH (actor:Person)-[role:ACTED_IN]->(movie:Movie) WHERE actor.name="Tom Hanks" RETURN movie.title
```

* la liste des personnages du film "The Matrix"

![image](https://user-images.githubusercontent.com/73080397/226098123-ccb717d1-1a6b-4cf1-960d-3804116f286f.png)

```cypher
MATCH (actor:Person)-[role:ACTED_IN]->(movie:Movie)WHERE movie.title="The Matrix" RETURN role.roles
```

* La date de sortie de chaque film


![image](https://user-images.githubusercontent.com/73080397/226098231-e3ec48b4-2ae5-44a3-a680-d0e0942036bd.png)

```cypher
MATCH (movie:Movie) RETURN movie.title, movie.released
```





