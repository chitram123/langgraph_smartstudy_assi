We are building an AI assistant that can answer 2 types of questions:

Theory question: "What is langgraph?"
Coding question: "Write a python code to build a calculator"
What should this AI asst. do?
It should understand the type of question
It should send it to the correct specialist: Theory agent, coding agent
Graph Architecture
            User query
                |
            Classifier node
            /              \
           /                \
        Theory node        Coding node
          |                     |
       Output                Output 
Components:
Nodes: Python functions a. Classifier node: Decide the question type b. Theory node: Explain the concept c. Code node : Generate the code

State: shared memory between nodes which will be appended - dictionary state = { "question": "", "question_type": "", "answer":"" }

Edges: they define what should happen next a. Static edge: Always go next b. Condition edge: decision based routing

Project structure:
a. state.py: we will define a memory that will be shared between nodes: question, question_type, answer

b. prompts.py: Stores all prompts separately. which will take user input Instead of writing all prompts everywhere - "explain this...", we can centralize the prompts

c. nodes.py Bascially contains all business logic 3 functions- each nodes a. classifer_nodes() b. theory_node() c. coder_node()

d. graph.py Workflow orchestration where all the components are built and stitched together. E.g. how the graph will be formed, how it will be initalized, how it will be built, what will be the entry point, end point this file will create nodes, edges, routing, entry point LangGraph will be in graph.py

e. main.py User interaction layer a. take user input b. start the graph c. print final response In this we will see multiple functions like .compile(), .invoke()

