# RedisGraph
Tutorials

In this repository, we will be exploring the graph data structure in redis.
we will be installing the redisgraph using docker.
for that, make sure you install the docker in your system.
After that, we have to import the redisgraph image from the docker host.

```
docker pull redislabs/redisgraph:edge

```
And, after that we will be creating container of that image.

```
docker run -d --name redisgraph-edge -p 6379:6379 redislabs/redisgraph:edge 

```
-d in detached mode(in background) and name of container is redisgraph-edge and we are running this process in 6379 port.

now the container of image redisgraph is running in background.
lets access the redis cli to interact with it.

```
docker exec -it redisgraph-edge redis-cli
```
-it = interactive mode which which open the process in terminal view.
redisgraph-edge is the name of the container that we just created.
and we are trying to open the redis-cli process which is available inside that container.

# Graph Instructions Starts:

## Creating Node:


```
GRAPH.QUERY aliceLovesrita "CREATE (alice:Person {name: 'Alice'})-[:loves]->(rita:Person {name: 'Rita'})"
```
GRAPH.QUERY is the redis graph module.

aliceLovesrita is the name of the graph, if it is not created, it will create one.
{name: "value"}, inside curly bracket we are defining the keys and values which are the properties of each node.

CREATE keyword is used to create new node with or without relationships.

[:relationship] relationship is given inside the [] big bracket.
the relationship also can contain property.
Making it simple , we are not defining properties in this step!

From side relationship is given with '-' to relationship
And To side relationship is given with '->' from relationship.

#### Note: Person is the label of each node. meaning, each node can have unique labels.


### so, executing it, we have created one graph, which has 2 nodes and one relationship  between them.

## Lets perform Some operations in graph:

### show all properties of every node:

```
GRAPH.QUERY aliceLovesrita "MATCH (x) RETURN x"
```

here, (x) ,x is variable inside (), using MATCH keyword with variable enclosed in paranthesis, will match all the nodes in graph aliceLovesrita and will store the result in x.

### return specific property only:

```
GRAPH.QUERY aliceLovesrita "MATCH (x) RETURN x.value"
```

Remember, the value was the name of key that were defined in the property of node.
That key is what we are accessing here.

(x) matches every node and is returned to x variable, but while returning , we are only returning specific property of node.

### Querying on the basis of Relationship:

```
GRAPH.QUERY aliceLovesrita "MATCH (x)-[:loves]->(y) RETURN x.name, y.name"

```
here, (x) and (y) variable are representing any nodes in the graph which has a relationship named loves inbetween them.
and after that, the node information is stored in x and y variable.
and we are returning only the name property of each node.


