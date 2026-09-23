\# Basic Security Models



Security models provide frameworks for controlling access to information and protecting systems.



\## 1. Bell-LaPadula Model



The \*\*Bell-LaPadula model\*\* focuses mainly on \*\*confidentiality\*\*.



Its goal is to prevent unauthorized users from accessing information at a higher security level.



\### Main principles



\* \*\*No Read Up\*\* — A subject should not read information at a higher security level.

\* \*\*No Write Down\*\* — A subject should not write information to a lower security level.



\### Example



A user with a \*\*Confidential\*\* clearance should not be able to read information classified as \*\*Secret\*\*.



\---



\## 2. Biba Model



The \*\*Biba model\*\* focuses mainly on \*\*integrity\*\*.



Its goal is to prevent unauthorized modification of information.



\### Main principles



\* \*\*No Read Down\*\*

\* \*\*No Write Up\*\*



The model helps prevent information from lower-integrity sources from affecting higher-integrity systems.



\---



\## 3. Clark-Wilson Model



The \*\*Clark-Wilson model\*\* focuses on maintaining data integrity through:



\* Well-formed transactions

\* Separation of duties

\* Access controls

\* Auditing



\### Example



A financial transaction might require one employee to create it and another authorized employee to approve it.



\---



\## Why security models matter



Security models help organizations design access-control systems and determine:



\* Who can access information

\* What information they can access

\* What actions they can perform

\* How changes should be controlled



\## Quick comparison



| Model         | Main Focus                            |

| ------------- | ------------------------------------- |

| Bell-LaPadula | Confidentiality                       |

| Biba          | Integrity                             |

| Clark-Wilson  | Integrity and controlled transactions |



\## Key takeaway



> \*\*Bell-LaPadula → Confidentiality\*\*



> \*\*Biba → Integrity\*\*



> \*\*Clark-Wilson → Integrity through controlled transactions\*\*



