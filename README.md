# Einzelarbeit-AI
Thema: Optimisierung eines LLMs mittels RAG

Konkret: 
Ich verwende LlaMA um Fragen zu Geschichten zu beantworten, die es ansonsten nicht kennt.
Da LlaMA die Geschichten nicht kennt lese ich diese als PDF-files ein, encode Sie und speichere die Embeddings in eine Vektordatenbank.
Ebenfalls werden Textsegmente, die mit den Vektoren verknüpft sind in einem Index gespeichert.
Die User Frage kann nun ebenfalls encodet werden. Dadurch können die relevanten segmente aus dem Text herausgesucht, und zu einem Kontextstring zusammengefasst werden.
LlamMA kann nun mit dem zusätzlichen Kontext versorgt werden.

Methodik und Verwendete Tools:

--Notebook: "Multiple Text einlesen"--

Text einlesen:
Mit dem Modul os werden die PDF dateien im Verzeichnis aufgelistet. Mit dem Modul Fitz (PyMuPDF) wird das PDF als text eingelesen.
Der Text wird dann in segmente unterteilt.

Encoding:
Mit dem SentenceTransformer aus der Bibliothek sentence_transformers werden die Segmente encoded.

Embeddings in Datenbank speichern:
Mit faiss werden die Embeddings in eine Vektorendatenbank gespeichert.
Gleichzeitig werden die Textsegmente über ein Mapping mit den Embeddings verknüpft und in einem json-File gespeichert.

--Notebook: "Optimized_LlaMA"--

Userfrage einlesen:
Der User kann nun seine Frage zu einer Geschichte als String eingeben.
Das encoding wird wieder mit dem SentenceTransformer durchgeführt.

Relevante Segmente aufrufen:
das jason-File und die faiss-Datenbank werden nun geladen.
Mit Hilfe von numpy wird nun ein Array aus den Embeddings der Userfrage erstellt.
Die Embeddings der Frage können nun mit denen der Geschichten abgeglichen werden und somit die relevanten Textsegmente bestimmt werden.

API-Abfrage vorbereiten:
Die Userfrage und der relevante Kontext werden Llama nun zur Vefügung gestellt.

API-Abfrage durchführen:
Die Anfrage wird nun an die Llama API gesendet. Diese gibt die Antwort im json-Format zurück.
Die Antwort wird für den User geprinted.
  
  
