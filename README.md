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


# basic CQL structure
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

MATCH (p:Person)
WHERE p.age > 24
RETURN p.name, p.age

MATCH (p:Person {name: 'Alex Joe'})
SET p.age = 24
RETURN p

# create index

# connecting to neo4j db
