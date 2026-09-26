# PROMPTS FOR THEMATIC ANALYSIS IN LLM MODELS
These are the prompts used as inputs for LLM models to assist with the thematic analysis in the master's thesis "Impacto do Trabalho Remoto na Dinâmica de Equipa no Desenvolvimento de Jogos Digitais"

## Prompt to Infer Initial Codes (Phase 2)
```
You are assisting with an inductive thematic analysis of semi-structured interviews, following Braun & Clarke's (2006) six-phase framework.

The study investigates how remote work impacts team collaboration in an indie game development studio (Nerd Monkeys, Portugal).

Your task for this transcript:
1. Read the full transcript carefully.
2. Identify meaningful excerpts relevant to the research question.
3. For each excerpt, suggest an initial code (a short label describing what the excerpt is about, always in english, remember the codes should be concise, descriptive, and capture the essence of the data).
4. Do NOT group into themes yet, only generate codes.
5. Present the output as a table:
[Excerpt | Code | Page/Line reference]

Be inductive, do not force codes into pre-existing categories. Let the data speak.

----------
PARTICIPANT ID: [ID]
ROLE: [Role]
STATUS: [Works or no Longer works in the studio]
TIME AT COMPANY: [Time interval]
WORK MODEL: [If worked remote only, or both remote and in person at the studio]
INTERVIEW DATE: [Date]
LANGUAGE: [Language of the transcript]
----------

TRANSCRIPT:
[Here, the anonymized transcript was pasted]
```

## Prompt to Find Similar Codes (Intermediate Step)
```
You are assisting with a qualitative coding consolidation task. Your role is STRICTLY to find matches between two tables. DO NOT generate new codes. DO NOT create themes. DO NOT summarize. DO NOT add any information not present in the input tables.

----------

INPUT TABLES:
TABLE A - "Filtered Codes" (researcher-validated reference):
Columns (Delimited by ';'): Final Code;IDs;Description
TABLE B -  "Unfiltered Codes" (batch to be processed):
Columns (Delimited by ';'): Excerpt;Code;ID

----------

YOUR TASK:
For each row in TABLE B, find which "Final Code" from TABLE A is semantically similar to the "Code" in TABLE B.
Use the "Description" in TABLE A and the "Excerpt" in TABLE B to help disambiguate meaning when the code labels alone are not enough.

----------

STRICT OUTPUT RULES, READ CAREFULLY:
RULE 1 - COLUMN VALUES:
- Column 1 "Final Code": copy EXACTLY the text from the "Final Code" column of TABLE A. Never write the Code from TABLE B here.
- Column 2 "ID": copy EXACTLY the ID from TABLE B (the unfiltered code being matched).
- Column 3 "Confidence": write exactly one of these four values: High / Medium / Low / No match.

RULE 2 -  ONE ROW PER TABLE B ENTRY:
Every single row in TABLE B must appear in the output exactly once. No row can be skipped. No row can appear more than once UNLESS it matches multiple Final Codes (in that case, create one output row per match).

RULE 3 - NO MATCH:
If no Final Code in TABLE A matches a TABLE B code, write "No match" in column 1 and leave column 2 as the TABLE B ID and column 3 as "No match".

RULE 4 - COUNT VERIFICATION:
After the table, write:
"TABLE B rows received: [X]"
"Output rows produced: [Y]"
"Rows with at least one match: [Z]"
"Rows with no match: [W]"
Where X must equal the number of rows in TABLE B that you received. Count them explicitly before starting.

RULE 5 - NO COMMENTARY:
Do not write any text outside the output table and the count verification. No explanations, no summaries, no suggestions. 

----------

CONFIDENCE LEVELS:
- High: clear and direct semantic match, you are certain
- Medium: plausible match but with some ambiguity
- Low: possible match but uncertain, flag for human review
- No match: nothing in TABLE A is similar

----------

OUTPUT FORMAT:

| Final Code (from Table A) | ID (from Table B) | Confidence |
|---|---|---|
| [exact text from TABLE A "Final Code" column] | [ID from TABLE B] | [High/Medium/Low/No match] |

----------

TABLE A - Filtered Codes:
[paste here: Final Code;IDs;Description]

----------

TABLE B - Unfiltered Codes::
[paste here: Excerpt;Code;ID]
```

## Prompt to Merge Codes and Infer Initial Themes (Phase 3) 
```
You are assisting with Phase 3 ("Searching for themes") of Braun & Clarke's (2006) six-phase thematic analysis framework. You have a folder with some scientific references that might provide methodological hints on how to proceed in this task. Also ground your decisions on the methodology for thematic analysis and, specifically, on the methodologies leveraging LLMs for this purpose. You will also find content regarding principles to adopt for codes, themes, and their genesis.

INPUT TABLE:
There is a file, codes.md, containing a list of the codes already extracted from the interviews along with a brief description of each code in two columns:
- "Code Name": the label of the consolidated code
- "Description": a brief explanation of what the code represents

The research question that is in focus is: "How does remote work impact team collaboration patterns in game development studios, and what tools and practices mitigate identified challenges?"

You will start from the list of codes and perform a deep analysis concerning the meaning and scope of each of the codes. You will create an Excel file that will be the target of all outcomes produced during your analysis and will
transfer the contents of codes.md into the first tab named "Initial Codes".

You will then perform analysis on potential code repetition or strong overlaps and propose merging any of the codes. For any merge, you will show the codes to merge, their meaning in the second column, and then the rationale in a third column and the name of the resulting code in the next column. This should all be depicted in a second tab of the Excel file named "Codes Merging".

A third tab, named "Stripped Code List" should contain just a listing of the codes after merging and their description.

Next, you will generate themes from the codes. You will abide by the definition of what a theme should be, in qualitative analysis and referring to Braun & Clarke and the documents in the reference bibliography for inductive processes. You will create a fourth tab in the Excel containing the Themes, sub-themes (if it makes sense), and the covered codes.

You will always abide by scientific standards and the relevant literature. Before starting the task, you will ask three questions that clarify any aspects that are not clear from the instructions.
```
