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

```
