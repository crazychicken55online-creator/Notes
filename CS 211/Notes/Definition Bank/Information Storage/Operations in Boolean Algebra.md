# NOT (' or ⇁ or ~)
- Represents negation, turns 0 (false) to 1 (true), and 1 (true) to 0 (false).
- Does not require a second bit, not is applied to the same bit.

| ⇁   |     |
| --- | --- |
| 0   | 1   |
| 1   | 0   |
# AND (& or . or ∧)
- Represents conjunction, only satisfies the condition if both the values of the individual variables are true.
- 1 & 1 = True AND True = True, 1 & 0 = True AND False = False, 0 & 1 = False AND True = False, 0 & 0 = False AND False = False

| ∧   | 0   | 1   |
| --- | --- | --- |
| 0   | 0   | 0   |
| 1   | 0   | 1   |
# OR (| or + or ∨)
- Represents disjunction and only returns true if **at least** one input is true.
- 1 | 1 = True OR True = True, 1 | 0 = True OR False = True, 0 | 1 = False OR True = True, 0 | 0 = False OR False = False.

| ∨   | 0   | 1   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 1   | 1   | 1   |
# XOR, Exclusive OR (⊕ or ^)
- A form of disjunction and returns true if there are exactly an **odd** number of inputs that are true.
- 1 ^ 1 = True XOR True = False (not an odd number of inputs that are true), 1 ^ 0 = True XOR False = True, 0 ^ 1 = False XOR True = True, 0 ^ 0 = False XOR False = False.

| ⊕   | 0   | 1   |
| --- | --- | --- |
| 0   | 0   | 1   |
| 1   | 1   | 0   |

