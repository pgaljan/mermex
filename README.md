# Mermex
### Excel-based Mermaid editor

This [macro-free excel workbook](https://github.com/pgaljan/mermex/blob/main/mermex.xlsx) aids authoring, editing, and version control when working with Mermaid diagrams.

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
- Basic knowledge of mermaid [flowchart](https://mermaid.js.org/syntax/flowchart.html) and [sequence](https://mermaid.js.org/syntax/sequenceDiagram.html) diagram/chart construction
- Excel 365 (leverages VSTACK which is not available with other excel builds)

### Usage
Construct the diagrams in the main table on each tab.  Copy and paste the mermaid code into your editor of choice [example](https://mermaid.live/edit#pako:eNpVUTtPwzAQ_iuWJ5DShiaQthmQaFq6FIGAiaTDNbZji_ghx6Gqkvx3nJaBejp_j7vTdx0uNaE4xazWx5KDdWj3Xijk31OecSsaJ6HZo8nksd9Sh6RW9NSj1c1Wo4ZrY4Sqbi_61ShCWbcbZRQ5LtT3cKGys_9V0R6t8x0Yp83-P_N51D3a5OKN-_bXDLfUu55zBimDSQkWZWD3OMCSWgmC-NW70VBgx6mkBU59SSiDtnYFLtTgpdA6_XFSJU6dbWmAW0PA0bWAyoK8BjdEOG2xn1U3Hqw1EOq_HXYnM8ZU-UB8x1IrJqoRb23tYe6cadIwHOlpJRxvD9NSy7ARZMyU_yyTMImSBUQxTeYxPMQxKQ-z5YJF9zNG5nezCPAwBJie579cbnI-TYANqC-t5d9Swy-DyY2J)

All worksheets can be safely duplicated in the same workbook.

### Examples
#### Class diagrams
``` mermaid
classDiagram
direction LR

%% Relationships
card "0..1" -- "1" traveler
traveler "1" -- |> ticket
ticket "1" o-- "1..n" coupon
coupon "0..1" -- "0..1" available seat
coupon "1" .. "*" luggage
coupon "*" -- "1" flight
flight "*" -- "1" flightNumber
flightNumber "1..*" -- "1" airport : start
airport "1" -- "1..*" flightNumber : goal
flight "*" -- "1" planeModel
planeModel "1" o-- "n" seat : has
planeModel "1" -- "*" airplane
available seat "*" -- "1" seat

%% Members
card : -id
card : +miles
traveler : #DoB~date~
traveler : #name
ticket : +code
ticket : +number~str~
coupon : redemption~date~
coupon : class
coupon : standby~bool~
luggage : number~int~
luggage : weight~int~
airport : +name
flightNumber : +departure~utc~*
flightNumber : +desc
flightNumber : +type
flightNumber : +airline
flight : +boardingTime~utc~
flight : +flightPath~json~
planeModel : +description
planeModel : +picture~png~
seat : row~int~
seat : column~str~
seat : class~str~
airplane : +regNumber~str~$
airplane : +status
airplane : -nextMaintTime~utc~

%% Links
link luggage "https://mermaid.js.org/syntax/classDiagram.html" 

%% Notes
note "Airline Booking System" 
note for luggage "Try the link!" 

```

#### flow diagram
``` mermaid
flowchart TD
1(((fa:fa-bell start)))-->|1: start|2(step1)
2(step1)-->|2: goto step2|3[(fa:fa-database step2)]
3[(fa:fa-database step2)]-->2(step1)
4(step3)-->|3: goto step4|5(step4)
4(step3)-->|4: goto step1|2(step1)
4(step3)-->|5: goto step 1|3[(fa:fa-database step2)]
5(step4)-->|6: end|6(end)
```

#### entity diagram
``` mermaid
erDiagram

%% Entities
Manufacturer||--||Car : "1:*"
Car||--||Named-Driver : "1:1"
Person||--||Named-Driver : "1:1"
household||--||Person : "*:1"

%% Attributes
Named-Driver{
string carRegistrationNumber PK, FK
string driversLicense FK, UK
}
Car{
string make "my comment"
string model
json parts
%% no spaces allowed in attribute: reg number
string VIN UK
}
Person{
string driversLicense UK
json name
polygon serviceArea
string phone UK
string householdUUID FK
string personUUID PK
}
household{
string householdUUID PK
json address
string personUUID FK
}
```

#### gantt chart
``` mermaid
gantt

%% Setup
dateFormat dd-mmm
title Example GANTT
excludes weekends

%% Tasks
section Section 1
Task A : done, 29-Apr, 9d
Crit bug fix : crit, 01-May, 4d
Finish work : done, 05-May, 7d
section Section 2
Another Task : active, 12-May, 14d
section lastSection
document : active, 12-May, 3d
publish : milestone, 15-May, d
```
#### user journey
``` mermaid
journey

%% Title
title Customer Experience Lifecycle

%% Tasks
section Sales
Sales Engagement : 7 : sales
Discovery : 4 : presales
Price Negotiation : 1 : sales
section Delivery
Delivery timing : 5 : services
Installation : 4 : services
Knowledge Transfer : 3 : education, services
section Operation
HW Support : 5 : services
SW Support : 3 : services
SLA : 4 : logistics

```

#### quadrant
``` mermaid
quadrantChart

%% Quadrant Setup
title Good and Bad ideas  (https://xkcd.com/2929/)

%% Axis Setup
x-axis sounds good --> sounds bad
y-axis actually good --> actually bad

%% values
Always saying what you think: [0.3, 0.76]
Asbestos: [0.15, 0.85]
Bloodletting: [0.85, 0.95]
Combo washer dryers: [0.15, 0.45]
Crumple zones: [0.75, 0.25]
cutting pizza in squares: [0.59, 0.59]
Cutting sandwiches diagonally: [0.36, 0.36]
Diverging diamond interchanges: [0.7, 0.4]
Eating citrus fruit while at sea: [0.5, 0.22]
Extension cores with prongs on both ends: [0.5, 0.99]
Fake prank fire extinguishers: [0.98, 0.92]
Fecal transplants: [0.9, 0.05]
Heat pumps: [0.22, 0.04]
Heelies: [0.4, 0.6]
Laser eye surgery: [0.64, 0.05]
Leaded Gasoline: [0.2, 0.95]
Pizza: [0.24, 0.08]
Prequels: [0.1, 0.55]
Project Orion: [0.9, 0.6]
Putting mold on infections: [0.9, 0.15]
Replying to spammers: [0.56, 0.7]
sliced bread: [0.05, 0.15]
Solar cars: [0.05, 0.6]
soup: [0.5, 0.5]
Stair Kayaking: [0.75, 0.8]
Toasting sandwiches: [0.25, 0.2]
Wheels on luggage: [0, 0.05]
```

#### sequence
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


