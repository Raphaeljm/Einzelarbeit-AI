# Einzelarbeit-AI
Thema: Optimisierung eines LLMs durch RAG

Konkret: 
Ich verwende LlaMA um Fragen zu einer unbekannten Geschichte zu beantworten. 
Da LlaMA die Geschichte nicht kennt lese ich diese als PDF-file ein encode Sie und speichere die Embeddings in eine Vektordatenbank.
Ebenfalls werden Textsegmente, die mit den Vektoren verknüpft sind in einem Index gespeichert.
LlamMA kann nun mit dem zusätzlichen Kontext versorgt werden.

Methodik und Verwendete Tools:
