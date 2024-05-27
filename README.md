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
RamLovesSita is the name of the graph, if it is not created, it will create one.
{name: "value"}, inside curly bracket we are defining the keys and values which are the properties of each node.
[:relationship] relationship is given inside the [] big bracket.
the relationship also can contain property.
Making it simple , we are not defining in this step!

From side relationship is given with '-' to relationship
And To side relationship is given with '->' from relationship.

#### Note: Person is the label of each node. meaning, each node can have unique labels.


### so, executing it, we have created one graph, which has 2 nodes and one relationship  between them.

## Lets perform Some operations in graph:



