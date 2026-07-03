# OrionTraining and AthenaTraining
## DSLs in the Age of LLMs: A Practical Experience on Database Schema Management Languages
> This repository contains the artifacts associated with the paper
> *DSLs in the Age of LLMs: A Practical Experience on Database Schema Management Languages*.

The OrionTraining and AthenaTraining projects provide datasets, prompts, workflows, and examples used to evaluate large language models for the comprehension, transformation, and evolution of the Orion [1] and Athena [2] DSLs.

[1] Alberto Hernández Chillón, Meike Klettke, Diego Sevilla Ruiz, Jesús García Molina:
A Generic Schema Evolution Approach for NoSQL and Relational Databases. IEEE Trans. Knowl. Data Eng. 36(7): 2774-2789 (2024)
(https://ieeexplore.ieee.org/abstract/document/10420500)

[2] Alberto Hernández Chillón, Diego Sevilla Ruiz, Jesús García Molina: 
Athena: A Database-Independent Schema Definition Language. ER (Workshops) 2021: 33-42
(https://link.springer.com/chapter/10.1007/978-3-030-88358-4_4)

# Repository Structure
Each project follows the same internal organization, separating the training and testing phases, along with the corresponding prompts used. In addition, a conversation with the model is included, following the prompts that were executed. The corresponding n8n workflows are also provided, enabling the execution and reproduction of the complete process.

- **/**
    - 📁 **.AthenaTraining/**
        - 📁 Learning/
            - 📁 1-Step (Formal Definition)/
                - 📄 Formal Specification.txt
            - 📁 2-Step (Articles)/
                - 📄 Athena.png
                - 📄 ChapterAthena.pdf
                - 📄 DesignAthena.pdf
            - 📁 3-Step (Examples)/
                - 📁 CentroDeportivo/
                    - 📄 CentroDeportivo.athena
                    - 📄 CentroDeportivo.cql
                    - 📄 CentroDeportivo.js
                    - 📄 CentroDeportivo.sql
                - 📁 SoftwareDev/
                    - 📄 SoftwareDev.athena
                    - 📄 SoftwareDev.cql
                    - 📄 SoftwareDev.js
                    - 📄 SoftwareDev.sql
                - 📁 SoftwareProject/
                    - 📄 SoftwareProject.athena
                    - 📄 SoftwareProject.cql
                    - 📄 SoftwareProject.js
                    - 📄 SoftwareProject.sql
                - 📁 Umugram/
                    - 📄 Umugram.athena
                    - 📄 Umugram.cql
                    - 📄 Umugram.js
                    - 📄 Umugram.sql
                - 📁 Vigilancias/
                    - 📄 Vigilancias.athena
                    - 📄 Vigilancias.cql
                    - 📄 Vigilancias.js
                    - 📄 Vigilancias.sql
            - 📄 Prompt.txt
        - 📁 Testing/
            - 📁 Athena2Schema/
                - 📄 EduPlatform.athena
            - 📁 Schema2Athena/
                - 📄 Cassandra2Athena.cql
                - 📄 MongoValidator2Athena.js
                - 📄 NaturalLanguage2Athena.txt
                - 📄 SQL2Athena.sql
            - 📁 n8n workflows/
                - 📄 n8n-Athena-DeepSeek.json
                - 📄 n8n-Athena-OpenAI_GPT.json
            - 📄 Prompt.txt
    - 📁 **.OrionTraining/**
        - 📁 Learning/
            - 📁 1-Step (Formal Definition)/
                - 📄 Formal Specification.txt
            - 📁 2-Step (Articles)/
                - 📄 Athena.txt
                - 📄 ChapterAthena.pdf
                - 📄 DesignAthena.pdf
            - 📁 3-Step (Examples)/
                - 📁 GameTracker/
                    - 📄 GameTracker1.athena
                    - 📄 GameTracker2.athena
                    - 📄 GameTrackerChange.cql
                    - 📄 GameTrackerChange.cypher
                    - 📄 GameTrackerChange.js
                    - 📄 GameTrackerChange.orion
                    - 📄 GameTrackerChange.sql
                - 📁 RunningSong/
                    - 📄 RunningSong1.athena
                    - 📄 RunningSong2.athena
                    - 📄 RunningSong3.athena
                    - 📄 RunningSongChange.cql
                    - 📄 RunningSongChange.cypher
                    - 📄 RunningSongChange.js
                    - 📄 RunningSongChange.orion
                    - 📄 RunningSongChange.sql
            - 📄 Prompt.txt
        - 📁 Testing/
            - 📁 Orion2Schema/
                - 📄 EduPlatform.athena
                - 📄 EduPlatformChange.orion
            - 📁 Schema2Orion/
                - 📄 CQL2Orion.cql
                - 📄 MongoDB2Orion.js
                - 📄 Neo4j2Orion.cypher
                - 📄 SQL2Orion.sql
            - 📁 n8n workflows/
                - 📄 n8n-Athena-DeepSeek.json
                - 📄 n8n-Athena-OpenAI_GPT.json
            - 📄 Prompt.txt
    - 📁 **.M2T/**
        - 📁 Athena/
            - 📄 Athena2Cassandra.xtend
            - 📄 Athena2MongoDBShemaValidator.xtend
            - 📄 Athena2MySQL.xtend
        - 📁 Orion/
            - 📄 Orion2Cassandra.xtend
            - 📄 Orion2MongoDB.xtend
            - 📄 Orion2MySQL.xtend
            - 📁 utils/
                - 📄 MongoDBTransactionModule.xtend
                - 📄 SqlProcedureModule.xtend

## Reproducing the Experiments
To reproduce the experiments, import the corresponding n8n workflow into your n8n instance. Configure the workflow variables by selecting the target schema and the translation direction (DSL → DB or NL/DB → DSL). The workflows already include the prompt sequence, so once the variables have been configured, simply execute the workflow to reproduce the corresponding experiment.

## Training and Testing Prompts
The recommended way to reproduce the experiments is by using the provided **n8n workflows**, which automate the complete prompt execution process. 

For users who prefer to execute the experiments manually, each `Prompt.txt` file contains the sequence of prompts used during the training and evaluation phases. Individual prompts are separated by the delimiter `----`, allowing each interaction with the language model to be reproduced independently.

* **Learning** folder: Contains the prompts used to provide the model with the knowledge required to understand the structure and rules of each DSL and examples.
* **Testing** folder: Contains the prompts used to evaluate the language model's ability to understand and transform code between the DSLs and the supported database schemas.

## Example Conversations
You can see the example conversations here:
- Athena: https://chatgpt.com/share/689a0551-d5f4-800b-9adb-98eb7e14cfa4
- Orion: https://chatgpt.com/share/68961d20-1aa8-800b-b9bd-2eca64d7cf1f
