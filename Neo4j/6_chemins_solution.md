# 6. Les chemins (Paths)

Ecrire la requête qui permet d'afficher :

* Les acteurs et les réalisateurs de tous les films,le résultat doit rassembler à :

![image](https://user-images.githubusercontent.com/73080397/226099544-3e1e3e68-12f7-4954-ac39-1706947d4b59.png)

```cypher
MATCH (a)-[:ACTED_IN]->(m)<-[:DIRECTED]-(d) RETURN a.name, m.title, d.name
```

* Ecrire une version divisée de la même requête:

```cypher
MATCH (a)-[:ACTED_IN]->(m), (m)<-[:DIRECTED]-(d) RETURN a.name, m.title, d.name
```

* Afficher les noeuds de la même requête, le résultat doit ressembler à:

![image](https://user-images.githubusercontent.com/73080397/226103464-3a00e3d0-9b8d-4152-829d-c1c625f5dc24.png)

```cypher
MATCH p=(a)-[:ACTED_IN]->(m)<-[:DIRECTED]-(d) RETURN nodes(p)
```
* Afficher le résultat en graphe :

![image](https://user-images.githubusercontent.com/73080397/226103521-667292dd-896a-4761-a092-f37955d8b4e7.png)

*  Les réalisateurs qui ont joué dans leurs propres films 

![image](https://user-images.githubusercontent.com/73080397/226103599-20c33bc2-e2ad-4c5b-8bbe-4d1cc2b55153.png)

```cypher
MATCH (p:Person)-[:ACTED_IN]->(movie:Movie), (p:Person)-[:DIRECTED]->(movie:Movie) RETURN p.name, movie.title
```

 * Les films ou Keanu Reeves a joué le rôle de Neo

![image](https://user-images.githubusercontent.com/73080397/226104525-34870e2d-f431-4e75-be79-d58340af2f73.png)

* Les acteurs qui ont déjà joué dans un même film avec Tom Hanks, et le film dans lequel ils ont joué

![image](https://user-images.githubusercontent.com/73080397/226104594-cb234484-01c0-49cc-abd8-7f32a129ba53.png)

```cypher
MATCH (p1:Person) -[role:ACTED_IN] -> (movie), (p2:Person)-[:ACTED_IN] -> (movie) WHERE p1.name="Tom Hanks" RETURN p2.name, movie.title
```

* Les acteurs qui ont joué dans un même film avec Tom Hanks, ou avec Keanu Reeves :

![image](https://user-images.githubusercontent.com/73080397/226104846-cd36dc58-a58f-4898-98b2-0f544f6b8f4c.png)


```cypher
MATCH(actor:Person)-[:ACTED_IN]->(movie:Movie)<-[:ACTED_IN]-(p:Person) WHERE p.name="Tom Hanks" OR p.name="Keanu Reeves" RETURN actor.name
```

* Les acteurs du film « The Matrix » :

![image](https://user-images.githubusercontent.com/73080397/226104941-192bd715-d91b-428e-8abe-486105fe8f52.png)

```cypher
MATCH (p:Person)-[:ACTED_IN]->(movie{title: "The Matrix"}) RETURN p.name
```









