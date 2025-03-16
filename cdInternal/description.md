### **FIRST and FOLLOW Calculation in Compiler Design**

In compiler design, **FIRST** and **FOLLOW** sets are used in the construction of **parsing tables** for **LL(1) parsers**. They help in deciding which production to apply based on the next input symbol.

---

## **1. FIRST Set**
### ✅ Definition:
The **FIRST** set of a non-terminal \( X \) is the set of terminals that appear **as the first symbol** in the strings derived from \( X \).

### ✅ Rules to Compute FIRST:
1. **If \( X \) is a terminal** → `FIRST(X) = {X}`  
2. **If \( X \) is a non-terminal**:
   - If there is a production `X → ε`, then add `ε` to `FIRST(X)`.
   - If `X → Y₁ Y₂ ... Yₙ`, then add `FIRST(Y₁)` (excluding `ε`) to `FIRST(X)`.  
     - If `FIRST(Y₁)` contains `ε`, add `FIRST(Y₂)`, and so on.  
     - If all `Y₁, Y₂, ... Yₙ` derive `ε`, add `ε` to `FIRST(X)`.

### ✅ Example:
**Grammar:**
```
S → AB
A → a | ε
B → b | ε
```
**FIRST Sets:**
- `FIRST(A) = {a, ε}`
- `FIRST(B) = {b, ε}`
- `FIRST(S) = {a, b, ε}`

---

## **2. FOLLOW Set**
### ✅ Definition:
The **FOLLOW** set of a non-terminal \( X \) is the set of terminals that can appear **immediately after \( X \)** in a derivation.

### ✅ Rules to Compute FOLLOW:
1. **Start symbol:** Add `$` (end of input) to `FOLLOW(S)`, where `S` is the start symbol.  
2. **If a production is of the form `A → αBβ`:**  
   - Add `FIRST(β)` (excluding `ε`) to `FOLLOW(B)`.  
   - If `FIRST(β)` contains `ε`, add `FOLLOW(A)` to `FOLLOW(B)`.  
3. **If a production is of the form `A → αB`:**  
   - Add `FOLLOW(A)` to `FOLLOW(B)`.

### ✅ Example:
**Grammar:**
```
S → AB
A → a | ε
B → b | ε
```
**FOLLOW Sets:**
- `FOLLOW(A) = {b, $}`
- `FOLLOW(B) = {$}`
- `FOLLOW(S) = {$}`

---

## **3. Example Calculation**
**Grammar:**
```
S → AB  
A → a | ε  
B → b | ε  
```
### **Step 1:** Compute FIRST sets:
- `FIRST(A) = {a, ε}`
- `FIRST(B) = {b, ε}`
- `FIRST(S) = {a, b, ε}`

### **Step 2:** Compute FOLLOW sets:
- `FOLLOW(S) = {$}`  
- `FOLLOW(A) = {b, $}`  
- `FOLLOW(B) = {$}`  

---

## **4. Importance of FIRST and FOLLOW**
- **FIRST** set helps decide which production to apply when expanding a non-terminal.  
- **FOLLOW** set helps decide when to apply a production based on the next input symbol or to identify if a non-terminal can derive an empty string.  

---

### ✅ **Use in LL(1) Parsing Table:**
- If `A → α` is a production:
  - Place `A → α` in `M[A, a]` for each `a ∈ FIRST(α)`.
  - If `FIRST(α)` contains `ε`, place `A → α` in `M[A, b]` for each `b ∈ FOLLOW(A)`.