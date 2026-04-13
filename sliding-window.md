# Sliding Window Diagrams

---

## Diagram 1 — Array (T = 0s)

```mermaid
flowchart LR
    A1[1] --> A2[2] --> A3[3] --> A4[7] --> A5[8] --> A6[9] --> A7[9] --> A8[0]

    classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
    class A1,A2,A3,A4,A5,A6,A7,A8 base;
```

## Diagram 2 — Window shows small part (T = 3s)

```mermaid
flowchart LR
    A1[ ] --> A2[ ] --> A3[ ] --> A4[ ] --> A5[ ] --> A6[ ] --> A7[ ] --> A8[ ]

    classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class A1,A2 window;
    class A3,A4,A5,A6,A7,A8 base;
```

## Diagram 3 — No repeated full scans (T = 6s)

```mermaid
flowchart LR
    Scan1[Full Scan ❌]
    Scan2[Full Scan ❌]
    Scan3[Full Scan ❌]

    classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

    class Scan1,Scan2,Scan3 bad;
```

## Diagram 4 — Window moves right (T = 9s)

```mermaid
flowchart LR
    A1[ ] --> A2[ ] --> A3[ ] --> A4[ ] --> A5[ ] --> A6[ ] --> A7[ ] --> A8[ ]

    Move --> 

    classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class A2,A3 window;
    class A1,A4,A5,A6,A7,A8 base;
```

## Diagram 5 — Expand window (T = 12s)

```mermaid
flowchart LR
    A1[ ] --> A2[ ] --> A3[ ] --> A4[ ] --> A5[ ] --> A6[ ] --> A7[ ] --> A8[ ]

    classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class A2,A3,A4 window;
    class A1,A5,A6,A7,A8 base;
```

## Diagram 6 — Shrink window (T = 15s)

```mermaid
flowchart LR
    A1[ ] --> A2[ ] --> A3[ ] --> A4[ ] --> A5[ ] --> A6[ ] --> A7[ ] --> A8[ ]

    classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class A3,A4 window;
    class A1,A2,A5,A6,A7,A8 base;
```

## Diagram 7 — Reuse overlap (T = 18s)

```mermaid
flowchart LR
    Old[Old Window]
    New[New Window]

    Overlap[Reuse]

    Old --> Overlap --> New

    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class Old,New,Overlap window;
```

## Diagram 8 — Valid window (T = 21s)

```mermaid
flowchart LR
    Window[Valid Window]

    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class Window window;
```
## Diagram 9 — Adjust window (T = 24s)

```mermaid
flowchart LR
    Left <-- Window --> Right

    classDef window fill:#facc15,stroke:#a16207,color:#000000;

    class Window window;
```

## Diagram 10 — Final idea (T = 27s)

```mermaid
flowchart LR
    Build --> KeepValid --> Adjust

    classDef step fill:#22c55e,stroke:#14532d,color:#ffffff;

    class Build,KeepValid,Adjust step;
```
