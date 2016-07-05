# Learn Neo4j [WORK IN PROGRESS!]
#### _Build scalable databases that leverage relationships between data_
![neo logo](http://info.neo4j.com/rs/773-GON-065/images/neo4j_logo.png)

## _Why_?

Neo4j harnesses the power of connections between data. It provides an _efficient_ and _intuitive_ way of working with data by mimicking how we _naturally_ think about it.  
* **Performance** - extremely scalable, performance remains the same as your data grows
* **Flexibility** - the database can be added to without endangering current functionality

#### Popular Use Cases

* Fraud detection
* Real-time recommendation engines
* Master data management
* Identity and access management
* Related search

## _What_?

> #### "A highly scalable native graph database that leverages data relationships as first-class entities"

A graph database can store any kind of data using a few simple concepts:

1. Nodes - graph data records
2. Relationships - connect nodes (_always have a direction and type_)
3. Properties - named data values

Neo4j can be queried for **_nodes_** (_objects in the graph_) and **relationships** (connections between objects_) with **Cypher** (_Neo4j's query language_).

![nodes and edges](https://cloud.githubusercontent.com/assets/12450298/16585645/defdd050-42b9-11e6-9315-827f355b3d1a.png)
_Both nodes and relationships can have name-value properties attached to them that can be used to give a more declarative description of what they are._


### Background Links

* Neo4j website https://neo4j.com/
* Youtube https://www.youtube.com/watch?v=Yzbk6VaavoM

## _Who_?

Neo4j is perfect for those who are particularly concerned with _not only_ the storage and retrieval of, but the _connections_ and _relationships_ between data.

## Getting Started

Follow these steps to get up and running with your first Neo4j database:

1. Download **[Neo4j](https://neo4j.com/)** and follow the installation instructions for your OS on the page that it takes you to after you click _download_ (_choose the community version if it's for personal use_)
![download neo4j](https://cloud.githubusercontent.com/assets/12450298/16585874/ca9bacda-42ba-11e6-977f-c2dc6f4b582b.png)
![installation](https://cloud.githubusercontent.com/assets/12450298/16586081/f4c1e550-42bb-11e6-8c6d-45ed4f361330.png)

2. After you've followed the installation instructions, you can then start Neo4j which will then give you a local url that you can paste in your browser
![local url](https://cloud.githubusercontent.com/assets/12450298/16586263/d9a45e96-42bc-11e6-9f56-769494e5e5d9.png)

3. Enter the default login details - `username = neo4j` `password=neo4j` you'll then be prompted to update your password
![change password](https://cloud.githubusercontent.com/assets/12450298/16586319/26b28096-42bd-11e6-92a9-66d974826cab.png)

4. You should then see that you've successfully connected to Neo4j
![connect neo4j](https://cloud.githubusercontent.com/assets/12450298/16586383/8860fe26-42bd-11e6-9cb0-1aaefbc15971.png)

5. There are also a couple of great tutorial resources/slideshows that you can look at if you click on the dashboard on the left or the 'Start learning' button in the middle of the page. They will give you a bit of background information on **Neo4j** and **Cypher**
![dashboard](https://cloud.githubusercontent.com/assets/12450298/16586444/df7407da-42bd-11e6-86d9-e122f03d4e3e.png)

## **Cypher** - Query language for Neo4j
Cypher is a very declarative query language meaning that you describe what you want to find, not how you want to find it. Let's look at a few examples of how we might implement it:

CREATE - create a node:

`$ CREATE (d:Person { name: "David", from: "Canada" })`

Now let's break the pieces down:

**CREATE** - claus to create data  
**()** - parentheses to indicate a node  
**d:Person** - a variable _'d'_ and label _'Person'_
**{}** - brackets to add properties to a node

Essentially we've just created a node **_person_** with a label of **_Person_** with the properties **_name: "David"_** and **_from: "Canada"_**.

MATCH - find a node:

`$ MATCH (d:Person) WHERE person.name = "David" RETURN d;`

**MATCH** - clause to specify a pattern of nodes and relationships  
**(d:Person)** a single node pattern with label 'Person' which will assign matches to the variable 'd'  
**WHERE** clause to constrain the results  
**d.name = "David"** - compares name property to the value "David"  
**RETURN** - clause used to request particular results

CREATE clauses can create multiple nodes and relationships at once:

```
$ MATCH (d:Person) WHERE d.name = "David"    
CREATE (j:Person { name: "John", from: "Sweden", learn: "surfing" }),  
(i:Person { name: "Ian", from: "England", title: "author" }),  
(r:Person { name: "Rick", from: "Belgium", pet: "Orval" }),  
(a:Person { name: "Allison", from: "California", hobby: "surfing" }),  
(d)-[:KNOWS {since: 2001}]->(j),(d)-[:KNOWS {rating: 5}]->(i),  
(j)-[:KNOWS]->(i),(j)-[:KNOWS]->(r),  
(i)-[:KNOWS]->(j),(i)-[:KNOWS]->(a),  
(r)-[:KNOWS]->(a)
```

Here we're creating 4 more nodes _(people)_ and then creating 6 relationships between them. Note that each relationship has a direction notated by `->`. Just like with nodes, we can add properties to the relationships using curly braces:

`(d)-[:KNOWS {since: 2001}]->(j)`
