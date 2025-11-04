# Requirements Validation 

# Consistency & Completeness Checks

| Code | Requirement Name | Validation Status | Rationale |
| :--- | :--- | :--- | :--- |
| **FR-1** | NFC Integration | Valid | Direct and relevant and cohesive with **NFR-1 (Access Speed)**. |
| **FR-2** | Database | Consistent | Aligns with the initial technical approach and ensuring predictable data handling. |
| **FR-3** | Terminal (GUI) | Valid | Essential operational component. |
| **FR-3a** | Authentication | Consistent | Consistent with the IP and Geo-based constraints and complements **NFR-3 Security** |
| **FR-3b** | Access Log | Valid | Necessary for tracking access and managing data confidentiality (**NFR-3**). |
| **FR-3c** | Secondary (Backup) Retrieval Method | Valid | Required to meet **NFR-5 Reliability** requirements. Also adds versatility to data access |
| **FR-3d** | Document Validation | Valid | Ensures **data quality and integrity** before storage, fulfilling the fundamental integrity need. |
| **FR-3e** | Backup and Recovery | Valid | Addresses the **Archive Halt Risk** and provides continuous system reliability (**NFR-5**). |
| **FR-3f** | Multiple Language Support | Consistent | Maybe useful in a multilingual organizations; correctly classified as low priority (**Superfluous**). |
| **FR-3g** | Theme Options | Consistent | Does not conflict with core requirements; correctly classified as low priority (**Superfluous**). |
| **NFR-1** | Access Speed | Consistent | Supported by the implementation of **FR-1 (NFC Integration)**, which ensures data delivery meets the time constraint. |
| **NFR-2** | Integration | Valid | Supports maintainability and ease of use. |
| **NFR-3** | Security | Consistent | Mandatory constraint that is enforced by the strict policies defined in **FR-3a (Authentication)** and addresses the sensitive confidentiality of the data. |
| **NFR-4** | Simplicity | Valid | Increases effeciency and facilitates adoption. |
| **NFR-5** | Reliability | Valid | Foundational requirement that supports **FR-3e** and ensures system availability against failure. |

# Requirements Risks

-**Risk 1 (R-1)** Bridge Failure: The bridge connecting the NFC-Reader to the web based system may be prone to failure. <br>
    **Consequence:** Reduced reliability and efficiency of the system; violating **NFR-1** and **NFR-5**. <br>
-**Risk 2 (R-2)** Access Speed Lag: The data transfer speed may slow down under load. <br>
    **Consequence:** Reduced efficiency of the system and nullifies the novelty; violating **NFR-1**. <br>

# Validation Methods

-**(R-1)** The creation of a MVP prototype and designing test cases to find any possible shortcomings on the system. <br>
      **Pass Condition:** System must function for 500 requests in a row. <br>
-**(R-2)** Creating "Stress Tests" and finding any possible bottlenecks then engineering resolutions to any issue. <br>
      **Pass Condition:** Data is transmitted within 10 seconds under a variety of the traffic/load on the network or the database.
