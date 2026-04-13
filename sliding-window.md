# Sliding Window

---

## Diagram 1 — (0s: Array Introduction)

“Imagine a moving window on an array”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;

class A1,A2,A3,A4,A5,A6 base;
```

---

## Diagram 2 — (3s: Many Subarrays = Problem)

“Why do we need this?”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

sub1([Start 0]) --> sub2([Start 1]) --> sub3([Start 2]) --> sub4([Start 3])

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class A1,A2,A3,A4,A5,A6 base;
class sub1,sub2,sub3,sub4 bad;
```

---

## Diagram 3 — (6s: Goal)

“We want the longest part with sum ≤ 5”

```mermaid
flowchart LR
goal[Find longest subarray<br/>Sum ≤ 5]

classDef good fill:#22c55e,stroke:#14532d,color:#ffffff;

class goal good;
```

---

## Diagram 4 — (9s: Brute Force = Repetition)

“Basic way repeats work again and again”

```mermaid
flowchart LR
A([Start at 0]) --> B([Check all])
C([Start at 1]) --> D([Check all])
E([Start at 2]) --> F([Check all])

X1((✖)) --> B
X2((✖)) --> D
X3((✖)) --> F

classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class A,B,C,D,E,F,X1,X2,X3 bad;
```

---

## Diagram 5 — (12s: Introduce Window)

“So we use a window”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

W1[[Window]]

W1 --- A1

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class A1,A2,A3,A4,A5,A6 base;
class W1 window;
```

---

## Diagram 6 — (15s: Expand Window)

“We expand to include more elements”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

W1[[Window]] --- A1 --- A2 --- A3

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class A1,A2,A3 window;
class A4,A5,A6 base;
class W1 window;
```

---

## Diagram 7 — (18s: Condition Breaks)

“Now sum becomes more than 5”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

W1[[Window]] --- A1 --- A2 --- A3

sum[Sum = 6 ❌]

sum --> W1

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;
classDef bad fill:#ef4444,stroke:#7f1d1d,color:#ffffff;

class A1,A2,A3 window;
class A4,A5,A6 base;
class W1 window;
class sum bad;
```

---

## Diagram 8 — (21s: Shrink from Left)

“So we shrink from the left”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

remove((Remove Left)) --> A1

W1[[Window]] --- A2 --- A3

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;

class A2,A3 window;
class A1,A4,A5,A6 base;
class W1 window;
```

---

## Diagram 9 — (24s: Valid Again)

“Now it becomes valid again”

```mermaid
flowchart LR
A1[2] --- A2[1] --- A3[3] --- A4[2] --- A5[1] --- A6[2]

W1[[Window]] --- A2 --- A3

sum[Sum = 4 ✅]

sum --> W1

classDef base fill:#3b82f6,stroke:#1e3a8a,color:#ffffff;
classDef window fill:#facc15,stroke:#92400e,color:#000000;
classDef good fill:#22c55e,stroke:#14532d,color:#ffffff;

class A2,A3 window;
class A1,A4,A5,A6 base;
class W1 window;
class sum good;
```

---

## Diagram 10 — (27s: Expand + Shrink)

“Expand… then shrink if needed”

```mermaid
flowchart LR
expand((Expand →)) --> mid[[Window]]
shrink((← Shrink)) --> mid

classDef window fill:#facc15,stroke:#92400e,color:#000000;

class mid window;
```

---

## Diagram 11 — (30s: Keep Moving Forward)

“We don’t restart… we adjust”

```mermaid
flowchart LR
step1[[Window]] --> step2[[Window]] --> step3[[Window]]

classDef window fill:#facc15,stroke:#92400e,color:#000000;

class step1,step2,step3 window;
```
