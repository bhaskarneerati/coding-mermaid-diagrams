# Sliding Window

---

## Diagram 1 — (0s: Moving Window on Array)

“Imagine a moving window on an array”

```mermaid
flowchart LR
A1[2] --> A2[1] --> A3[3] --> A4[2] --> A5[1] --> A6[2]

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class A1,A2,A3,A4,A5,A6 base;
```

---

## Diagram 2 — (3s: Many Subarrays)

“Why do we need this?”

```mermaid
flowchart LR
S1[2] --> S2[1] --> S3[3] --> S4[2] --> S5[1] --> S6[2]

sub1([2,1]) --> sub2([1,3]) --> sub3([3,2])

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class S1,S2,S3,S4,S5,S6 base;
class sub1,sub2,sub3 bad;
```

---

## Diagram 3 — (6s: Problem Condition)

“We want the longest part with sum ≤ 5”

```mermaid
flowchart LR
C1[2] --> C2[1] --> C3[3] --> C4[2] --> C5[1] --> C6[2]
cond[Sum ≤ 5]

cond --> C3

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef good fill:#22c55e,stroke:#14532d,color:#ffffff;

class C1,C2,C3,C4,C5,C6 base;
class cond good;
```

---

## Diagram 4 — (9s: Repeated Work)

“Basic way repeats work again and again”

```mermaid
flowchart LR
R1[2] --> R2[1] --> R3[3] --> R4[2] --> R5[1] --> R6[2]

subA([2,1,3]) --> subB([1,3,2]) --> subC([3,2,1])

X1((✖)) --> subA
X2((✖)) --> subB
X3((✖)) --> subC

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class R1,R2,R3,R4,R5,R6 base;
class subA,subB,subC,X1,X2,X3 bad;
```

---

## Diagram 5 — (12s: Start Window)

“So we use a window”

```mermaid
flowchart LR
W1[2] --> W2[1] --> W3[3] --> W4[2] --> W5[1] --> W6[2]

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class W1 window;
class W2,W3,W4,W5,W6 base;
```

---

## Diagram 6 — (15s: Expand Window)

“We expand to include more elements”

```mermaid
flowchart LR
E1[2] --> E2[1] --> E3[3] --> E4[2] --> E5[1] --> E6[2]

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class E1,E2,E3 window;
class E4,E5,E6 base;
```

---

## Diagram 7 — (18s: Condition Breaks)

“Now sum becomes more than 5”

```mermaid
flowchart LR
B1[2] --> B2[1] --> B3[3] --> B4[2] --> B5[1] --> B6[2]

sum[Sum = 6]

sum --> B2

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;
classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class B1,B2,B3 window;
class B4,B5,B6 base;
class sum bad;
```

---

## Diagram 8 — (21s: Shrink Window)

“So we shrink from the left”

```mermaid
flowchart LR
S1[2] --> S2[1] --> S3[3] --> S4[2] --> S5[1] --> S6[2]

arrow((→))

arrow --> S2

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class S2,S3 window;
class S1,S4,S5,S6 base;
```

---

## Diagram 9 — (24s: Valid Again)

“Now it becomes valid again”

```mermaid
flowchart LR
V1[2] --> V2[1] --> V3[3] --> V4[2] --> V5[1] --> V6[2]

sum[Sum = 4]

sum --> V3

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;
classDef good fill:#22c55e,stroke:#14532d,color:#ffffff;

class V2,V3 window;
class V1,V4,V5,V6 base;
class sum good;
```

---

## Diagram 10 — (27s: Expand + Shrink)

“Expand… then shrink if needed”

```mermaid
flowchart LR
M1[2] --> M2[1] --> M3[3] --> M4[2] --> M5[1] --> M6[2]

left((←)) --> M2
right((→)) --> M3

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class M2,M3,M4 window;
class M1,M5,M6 base;
```

---

## Diagram 11 — (30s: Continuous Adjustment)

“We don’t restart… we adjust”

```mermaid
flowchart LR
C1[2] --> C2[1] --> C3[3] --> C4[2] --> C5[1] --> C6[2]

move1((→)) --> C2
move2((→)) --> C3
move3((→)) --> C4

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class C3,C4,C5 window;
class C1,C2,C6 base;
```
