# Professional Social Network in Neo4j

## Objective

The objective of this assignment is to build a graph database using Neo4j that represents a professional social network. This graph will contain nodes for people, companies, projects, skills, cities, and events, with relationships connecting these entities. The goal is to create the graph, insert data, and then execute Cypher queries to analyze the network.

## Requirements

1. **Neo4j**: You must have Neo4j installed and running on your machine.
   - Install Neo4j: [Neo4j Download](https://neo4j.com/download/)
   - Start Neo4j and access the Neo4j Browser interface at `http://localhost:7474`.

2. **Neo4j Browser**: Use the Neo4j browser to create nodes and relationships, and execute Cypher queries.

## Graph Database Schema

### 1. Nodes:
The graph will consist of the following types of nodes, with their corresponding properties:

- **Person**: Represents individuals in the network. Properties:
  - `name` (string): The name of the person.
  - `age` (integer): The person's age.
  - `title` (string): The person's job title.

- **Company**: Represents companies where people work. Properties:
  - `name` (string): The name of the company.

- **Project**: Represents projects that people have worked on. Properties:
  - `name` (string): The name of the project.

- **Skill**: Represents skills that people possess. Properties:
  - `name` (string): The name of the skill.

- **City**: Represents the city where a person lives or where a company is located. Properties:
  - `name` (string): The name of the city.

- **Event**: Represents professional events or conferences attended by people. Properties:
  - `name` (string): The name of the event.

### 2. Relationships:
The graph will have the following relationships connecting the nodes:

- **KNOWS**: Connects two Person nodes to indicate that they know each other.
- **WORKS_FOR**: Connects a Person to a Company to indicate where they work.
- **LIVES_IN**: Connects a Person to a City where they live.
- **LOCATED_IN**: Connects a Company to a City to indicate where it is headquartered.
- **WORKED_ON**: Connects a Person to a Project they contributed to.
- **HAS_SKILL**: Connects a Person to a Skill they possess.
- **ATTENDED**: Connects a Person to an Event they attended.
- **HOSTED_BY**: Connects an Event to a Company that hosted it.

## Queries

You will be tasked with answering the following questions using Cypher queries:

### 1. Question 1:
Find all people who live in “City” and work for “Company”.
- **Expected Output**: List of names of people who meet this condition.

### 2. Question 2:
Find events that were hosted by companies located in “City”.
- **Expected Output**: List of event names and the companies that hosted them.

### 3. Question 3:
Find people who have skills related to "Skill 1" or "Skill 2".
- **Expected Output**: List of names and their corresponding skills.

### 4. Question 4:
Find pairs of people who know each other and attended the same event.
- **Expected Output**: Pairs of names and the event they attended.

## Steps

### 1. Setup Neo4j

Ensure that Neo4j is installed and running on your system. Once Neo4j is up and running:

- Open the Neo4j browser (`http://localhost:7474`) and connect to your database.
- Start creating nodes and relationships based on the schema mentioned above.

### 2. Create Nodes and Relationships

- Use Cypher to insert data for **Person**, **Company**, **Project**, **Skill**, **City**, and **Event** nodes.
- Create relationships like **KNOWS**, **WORKS_FOR**, **LIVES_IN**, **LOCATED_IN**, **WORKED_ON**, **HAS_SKILL**, **ATTENDED**, and **HOSTED_BY**.

### 3. Write and Execute Queries

Use the Neo4j browser to write and execute the following queries based on the provided questions.

#### Example Queries

1. **Find all people who live in a specific city and work for a specific company**:

```cypher
MATCH (p:Person)-[:WORKS_FOR]->(c:Company), (p)-[:LIVES_IN]->(city:City)
WHERE city.name = 'City' AND c.name = 'Company'
RETURN p.name AS Person
