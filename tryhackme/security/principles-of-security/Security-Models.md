# Security Models

Security models provide formal ways of implementing security principles, including the three elements of the CIA Triad:

- **Confidentiality**
- **Integrity**
- **Availability**

## Bell-LaPadula Model

The **Bell-LaPadula model** is designed primarily to protect **confidentiality**.

It controls access to data based on security levels and follows the principle of restricting access on a need-to-know basis.

### Rules

- **No read up** — a subject cannot read data at a higher security level.
- **No write down** — a subject cannot write data to a lower security level.

### Common use

The model is particularly suited to environments such as military and government organisations where information is classified into different security levels.

---

## Biba Model

The **Biba model** is designed primarily to protect **integrity**.

It controls how users and systems can read and modify information based on security levels.

### Rules

- **No read down** — a subject cannot read data at a lower integrity level.
- **No write up** — a subject cannot write data to a higher integrity level.

### Common use

The Biba model can be useful in environments where maintaining the integrity and trustworthiness of information is particularly important, such as software development.

---

## Bell-LaPadula vs Biba

| Model | Primary goal | Read rule | Write rule |
|---|---|---|---|
| **Bell-LaPadula** | Confidentiality | No read up | No write down |
| **Biba** | Integrity | No read down | No write up |

### Easy way to remember

**Bell-LaPadula → Confidentiality**

> No read up, no write down.

**Biba → Integrity**

> No read down, no write up.

---

## Questions

### Q1. What is the name of the model that uses the rule "can't read up, can read down"?

**Answer:** `Bell-LaPadula`

The Bell-LaPadula model protects confidentiality by preventing subjects from reading data at a higher security level.

### Q2. What is the name of the model that uses the rule "can read up, can't read down"?

**Answer:** `Biba`

The Biba model protects integrity by restricting how information can be read and modified across security levels.

### Q3. If you were in the military, what security model would you use?

**Answer:** `Bell-LaPadula`

Bell-LaPadula is designed to protect confidentiality and is well suited to environments using classified information and security levels.

### Q4. If you were a software developer, what security model would the company perhaps use?

**Answer:** `Biba`

Biba focuses on maintaining data integrity, which can be important in software development environments.

---

## Key Takeaway

**Bell-LaPadula → Confidentiality → No read up, no write down**

**Biba → Integrity → No read down, no write up**
