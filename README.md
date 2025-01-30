# neo4j_au_project
this is a tutorial guide for onboarding new members join the project for the neo4j database
You can download neo4j desktop here https://neo4j.com/download/

# instructions of installation
Youtube videos parts walkthrough how to install and set up project with apoc: https://www.youtube.com/watch?v=y2V-i5D2D64&ab_channel=AgigaQuanta

# onboarding guide
full lesson (6 hours)
https://youtu.be/_IgbB24scLI?si=jHdiTSHtJvjfTNRn

official lesson
https://graphacademy.neo4j.com/courses/neo4j-fundamentals/

sandbox test databases
https://neo4j.com/docs/getting-started/appendix/example-data/

getting started with movies test db and basic sample CQL code to retreive data
https://neo4j.com/developer-blog/getting-started-with-play-movies/

basic queries guide
https://neo4j.com/docs/cypher-manual/current/queries/basic/

alter database queries
https://neo4j.com/docs/operations-manual/current/database-administration/standard-databases/alter-databases/

index guide
https://neo4j.com/docs/cypher-manual/current/indexes/search-performance-indexes/managing-indexes/?utm_source=GSearch&utm_medium=PaidSearch&utm_campaign=Evergreen&utm_content=AMS-Search-SEMCE-DSA-None-SEM-SEM-NonABM&utm_term=&utm_adgroup=DSA&gad_source=1&gclid=CjwKCAiAneK8BhAVEiwAoy2HYY7l_YuVAVgQqAdsN7hiBkWqBPir55lYzqYpTNCj6AP7liSlPdYhphoCXbkQAvD_BwE

connecting neo4j to react
https://medium.com/neo4j/connecting-to-react-app-to-neo4j-148881d838b8

# basic CQL structure
create database:
CREATE (n:Label {property: value});
MATCH (a:Label1), (b:Label2);
WHERE n.property = value;
RETURN n;

CREATE (n:Person)
CREATE (n:Person {
    name: 'Alex Joe',
    age: 24,
    email: 'Alex@123.com'
})

search on property:
MATCH (p:Person)
WHERE p.age > 24
RETURN p.name, p.age

MATCH (p:Person {name: 'Alex Joe'})
SET p.age = 24
RETURN p

# create index

range index

CREATE INDEX node_range_index_name IF NOT EXISTS FOR (n:Person) ON (n.surname)

CREATE INDEX composite_range_node_index_name FOR (n:Person) ON (n.age, n.country)

text index:

CREATE TEXT INDEX node_text_index_nickname FOR (n:Person) ON (n.nickname)

CREATE TEXT INDEX rel_text_index_name FOR ()-[r:KNOWS]-() ON (r.interest)

point index:

CREATE POINT INDEX node_point_index_name FOR (n:Person) ON (n.sublocation)

CREATE POINT INDEX rel_point_index_name FOR ()-[r:STREET]-() ON (r.intersection)

**lookup index**:

Two token lookup indexes are created by default when creating a Neo4j database (one node label lookup index and one relationship type lookup index). Only one node label and one relationship type lookup index can exist at the same time. If a token lookup index has been deleted, it can be recreated with the CREATE LOOKUP INDEX command. Note that the index name must be unique.

CREATE LOOKUP INDEX node_label_lookup_index FOR (n) ON EACH labels(n)

CREATE LOOKUP INDEX rel_type_lookup_index FOR ()-[r]-() ON EACH type(r)

# connecting to neo4j db
import { Neo4jProvider, createDriver } from 'use-neo4j'
// Create driver instance
const driver = createDriver('neo4j', 'localhost', 7687, 'neo4j', 'letmein')

ReactDOM.render(
  <React.StrictMode>
    <Neo4jProvider 
      scheme="neo4j+s"
      host="myauradb.neo4j.io"
      port="7687"
      username="username"
      password="defaultpassword" 
      database="someotherdb"
     >
      <App />
    </Neo4jProvider>
  </React.StrictMode>,
  document.getElementById('root')
);

read this page for more details:
https://medium.com/neo4j/connecting-to-react-app-to-neo4j-148881d838b8
