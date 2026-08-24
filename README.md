# AMIA

```mermaid
graph TD 
A[AMIA Streamlit UI] -->|1. Sends User Query and selected Agent Pipeline| B[Orchestrator]

%% Check and invoke the correct pipeline %%
B-->C{Single<br/>Agent?}

%% Single Agent Pipeline %%
C-->|3. Yes: Query LLM for SWOT theme in User Query| D[Ollama]
D-->|4. Return Identified theme | B
B-->|5. Look up vector db with User Query and theme| E[(Chroma DB)]
E-->|6. Return chunks| B
B-->|7. Query LLM with User Query and RAG Context| D
D-->|8. Return Response|  A

```
