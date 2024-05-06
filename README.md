langgraph editor

This tool is designed to visually edit langgraph workflow. You can open the notebook in google's colab. 
Below is the interface of the tool. It is based on litegraph.js as its workflow engine. 
3 types of nodes are added, including LangGraphNode, LangGraphConditionalNode, and LangGraphEndNode.
When you finish editing the workflow, click "Compile" menu item to your design as a python file.

The workflow can be loaded/saved locally from/to /content/workflow.json.

<img src="https://raw.githubusercontent.com/Erickrus/langgraph-editor/main/snapshot.png" width=1080px />


```python
from langgraph.graph import END, StateGraph
workflow = StateGraph(GraphState)

# Define the nodes
workflow.add_node("query", query) # query
workflow.add_node("web_search", web_search) # web_search

# Build graph
workflow.add_conditional_edge(
    "query",
    decide,
    {
        "end": END,
        "web_search": "web_search",

    })
workflow.set_entry_point("query")
workflow.add_edge("web_search", END)

# Compile
app = workflow.compile()
```
