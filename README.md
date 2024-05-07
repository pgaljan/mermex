# Mermex
### Excel-based Mermaid editor

This [spreadhseet]([url](https://github.com/pgaljan/mermex/blob/main/mermex.xlsx)) aids authoring, editing, and version control when working with Mermaid diagrams.

### Key features:
- class diagrams
- flow diagrams with font awesome and autonumbering support
- entity diagrms 
- sequence diagrams with hashing and titling
- state diagrams
- quadrants
- gantt
- user journey

### Prerequisites
- Basic knowledge of mermaid [flowchart]([url](https://mermaid.js.org/syntax/flowchart.html)) and [sequence]([url](https://mermaid.js.org/syntax/sequenceDiagram.html)) diagram construction
- Excel 365 (leverages VSTACK which is not available with other excel builds)

### Usage
Construct the diagrams in the main table on each tab.  Copy and paste the mermaid code into your editor of choice [example](https://mermaid.live/edit#pako:eNpVUTtPwzAQ_iuWJ5DShiaQthmQaFq6FIGAiaTDNbZji_ghx6Gqkvx3nJaBejp_j7vTdx0uNaE4xazWx5KDdWj3Xijk31OecSsaJ6HZo8nksd9Sh6RW9NSj1c1Wo4ZrY4Sqbi_61ShCWbcbZRQ5LtT3cKGys_9V0R6t8x0Yp83-P_N51D3a5OKN-_bXDLfUu55zBimDSQkWZWD3OMCSWgmC-NW70VBgx6mkBU59SSiDtnYFLtTgpdA6_XFSJU6dbWmAW0PA0bWAyoK8BjdEOG2xn1U3Hqw1EOq_HXYnM8ZU-UB8x1IrJqoRb23tYe6cadIwHOlpJRxvD9NSy7ARZMyU_yyTMImSBUQxTeYxPMQxKQ-z5YJF9zNG5nezCPAwBJie579cbnI-TYANqC-t5d9Swy-DyY2J)

All worksheets can be safely duplicated in the same workbook.

### Examples
#### Class diagrams
``` mermaid
sequenceDiagram
autonumber

%% Actors
Participant authenticator
Actor user

%% Boxes

%% Diagram
loop 
user->>app: userID
app->>authenticator: open with userID
end 
alt has account
authenticator->>authenticator: map userID to cred
else no account
app-->>user: user onboard
end 
authenticator-->>user: password challenge
user->>authenticator: password
authenticator-->>user: otc challenge
user->>authenticator: one-time code
user->>authenticator: one-time code
destroy authenticator
authenticator->>app: token
app->>user: session established
Box gray front
Actor user
end
Box middle
Participant authenticator
end
```

#### flow diagram


#### entity diagram


#### gantt chart

#### user journey


#### quadrant


#### sequence



