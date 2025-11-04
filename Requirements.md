# Requirements


## Elicitation Techniques
1. Scenarios:
     The team derived multiple requirements (FR1 -> FR6, FR8) from the scenarios modeled from the users' perspectives this allowed the team to identify the system's key factors, requirments, and boundaries.
2. Brainstorming:
     The team utilized brainstorming to fill out the corners of the requirements field, the majority of the non-functional requirements were found using this technique.
   
## Scenario A
1. Official logs into his account
2. Civilian is asked to provide his archived files.  
3. Civilian takes out his ID and scans it on the official's desktop reader.  
4. Civilian's data is delivered directly to the official's desktop.
5. The official continues with the procedure and if there are any changes in the files they are sent to the archiver
6. Archiver recieves, verifies and updates data
---

## Scenario B
1. Civilian needs to save his documents to the archive
2. Civilian goes to the archiver and provides his documents
3. Archiver verifies and validates data before uploading it to the system
---

### System Requirements

1. **NFC Integration**  
   The system must bridge NFC capability to the web-based terminal that accesses the database.

2. **Database**  
   Originally using a structured database to store all required information with mySQL by storing the scanned document files on the server and keeping their paths on the database.
   Currently studying switching to a noSQL database instead of a structured database (more updates soon)

4. **Terminal (GUI)**  
   A GUI is needed to access and interact with the database in a user-friendly way.
   - **Authentication**: Require authentication for all access. Use IP & geo-based restrictions.  
   - **Access Log**: Record all user access and activity.  
   - **Secondary (Backup) Retrieval Method**: Include search, sort, and QR code as alternative access methods.  
   - **Document Validation**: All documents must be validated before being stored or retrieved.  
   - **Backup and Recovery**: Include data recovery in case of system failure.  
   - **Multiple Language Support**: The GUI should allow users to switch between different languages. *(Superfluous)*  
   - **Theme Options**: The GUI should offer multiple color themes (e.g., dark mode). *(Superfluous)*

---

### Structured Specification

### 1. FR-1: NFC Integration

| Field | Specification Detail |
| :--- | :--- |
| **Function** | **Retrieve Civilian Record Index via NFC Scan** |
| **Description** | Establishes communication with the Official's desktop NFC reader to securely extract the civilian's unique ID index and initiates a corresponding database lookup. |
| **Inputs** | Civilian ID (NFC Tag Data). |
| **Source** | Official's desktop NFC reader, which must be connected to the web terminal via a Python or Javascript API bridge. |
| **Outputs** | Civilian ID Index (The database lookup key). |
| **Destination** | FR-2 Database Query and FR-3 Terminal (GUI) display function. |
| **Action** | The API bridge transmits the raw NFC data to the web server, which performs validation. If valid, the Civilian ID Index is used to query the file paths in the database. |
| **Requires** | The NFC reader must be active and the API bridge must be running. |
| **Precondition** | Official must be successfully logged in (**FR-3a**) and the desktop reader must be operational. |
| **Postcondition** | The Official's GUI displays the list of documents corresponding to the Civilian ID index. |
| **Side effects** | None. |

### 2. FR-2: Database Optimization

| Field | Specification Detail |
| :--- | :--- |
| **Function** | **Store and Optimize Data Retrieval** |
| **Description** | Ensures the structured database is designed and maintained to prevent becoming a system bottleneck in terms of speed and capacity. |
| **Inputs** | Database records (user accounts, document paths, access logs, civilian indices). |
| **Source** | System Administrator (via maintenance commands) and Archiver (**Scenario B**). |
| **Outputs** | Optimized query execution and reduced latency. |
| **Destination** | All system functions requiring data access (FR-1, FR-3a, NFR-1). |
| **Action** | Database tables are indexed, queries are designed efficiently, and caching techniques are implemented to store frequently accessed data in memory. |
| **Requires** | System Administrator account (**FR-3a**) and system performance monitoring (**NFR-1**). |
| **Precondition** | Database structure must support indexing of the NFC-compatible Civilian ID addresses. |
| **Postcondition** | Performance logs confirm data delivery consistently meets the **NFR-1 (10-second)** constraint. |
| **Side effects** | Increased memory usage due to caching. |

### 3. FR-3a: Authentication

| Field | Specification Detail |
| :--- | :--- |
| **Function** | **Validate User Access Credentials and Location** |
| **Description** | Verifies the user's identity and confirms the access request originates from an authorized location and designated machine before granting terminal access. |
| **Inputs** | Username, Password, Request Geo-location, and Source IP Address. |
| **Source** | Official, Archiver, or Administrator user input. |
| **Outputs** | Access granted / Access denied. |
| **Destination** | FR-3 Terminal (GUI) login handler and FR-3b Access Log. |
| **Action** | The system verifies: 1) Valid username/password. 2) Geo-location is consistent with the database's expected location. 3) IP address matches the designated work desktop. |
| **Requires** | Secure connection (NFR-3). |
| **Precondition** | User attempts to access the web-based terminal interface. |
| **Postcondition** | **(Success)** Access Log entry created, GUI access granted. **(Failure)** Access Log entry created with "Denied" status, user remains on login screen. |
| **Side effects** | None. |

### Functional Requirements Table (FR)

| ID | Requirement | Description / Details | Priority | User (U) / System (S) | Justification |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **FR-1** | NFC Integration | The system must include NFC capability and bridge it with the web-based terminal to access the database. | Mandatory | **S** | The primary novelty of the system. |
| **FR-2** | Database | A structured database must store all user, document, and access data. | Mandatory | **S** | Core backbone of the system to hold all the data |
| **FR-3** | Terminal (GUI) | A graphical user interface (GUI) must allow officials to interact with the database in a user-friendly manner. | Mandatory | **U** | Required for officials and archivers to access the system. |
| **FR-3a** | Authentication | All access must require authentication with IP and geo-based restrictions. | Mandatory | **S** | Required to control access and protect sensitive data. |
| **FR-3b** | Access Log | The system must record all user access and actions in detailed logs. | Mandatory | **S** | Necessary for security audits and data integrity verification. |
| **FR-3c** | Secondary (Backup) Retrieval Method | The system must provide alternative retrieval options such as search, sort, and QR code access. | Nice to Have | **U** | Increases reliability but NFC is the primary, essential method. |
| **FR-3d** | Document Validation | All uploaded documents must undergo validation before being stored or retrieved. | Mandatory | **S** | Prevents corruption and ensures data quality at the source. |
| **FR-3e** | Backup and Recovery | The system must include mechanisms for data backup and recovery in case of failure or corruption. | Mandatory | **S** | Critical for maintaining system uptime and preventing data loss. |
| **FR-3f** | Multiple Language Support | GUI should allow users to switch between multiple languages. | Superfluous | **U** | A cosmetic/usability feature that doesn't affect the functionality of the system. |
| **FR-3g** | Theme Options | GUI should offer multiple color themes. | Superfluous | **U** | A purely cosmetic feature, non-essential to system operation. |

---

### Non-Functional Requirements Table (NFR)

| ID | Requirement | Description / Criteria | Priority | User (U) / System (S) | Justification |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **NFR-1** | Access Speed | The system must deliver requested data within a maximum of 10 seconds. | Mandatory | **S** | Required for officials to maintain acceptable operational workflow. |
| **NFR-2** | Integration | The system must operate through a single unified interface. | Mandatory | **S** | Ensures a cohesive system architecture. |
| **NFR-3** | Security | The system must ensure data confidentiality, integrity, and access control. | Mandatory | **S** | Non-negotiable constraint due to the sensitive nature of data. |
| **NFR-4** | Simplicity | The interface must be intuitive and easy to navigate for all user types. | Nice to Have | **U** | Enhances user adoption but the system can be functional without perfect simplicity. |
| **NFR-5** | Reliability | The system must remain stable, dependable, and versatile under various conditions. | Mandatory | **S** | Essential for continuous service and supports the Backup/Recovery (FR-3e). |

---
### Raw Requirements

| ID | Raw Requirement Description | Elicitation Source |
| :--- | :--- | :--- |
| **R-1** | The system must use NFC technology to retrieve civilian ID data. | Scenario A, FR-1 |
| **R-2** | A bridge (API) must connect the NFC reader to the web terminal. | FR-1 Detail |
| **R-3** | All data in the database must be indexed to support NFC address lookups. | FR-1 Detail |
| **R-4** | A structured database is required to store all user and document files. | FR-2 |
| **R-5** | The database must be optimized for speed, capacity, and organization. | FR-2 Detail |
| **R-6** | A GUI is needed for officials and archivers to access and interact with the data. | FR-3 |
| **R-7** | All access must require authentication (credentials, geo-location, and IP restrictions). | FR-3a |
| **R-8** | The system must record all user activity and access in a detailed log. | FR-3b |
| **R-9** | The Archiver must verify and validate documents before uploading them. | Scenario B, FR-3d |
| **R-10** | The GUI must provide alternative retrieval options, including search, sort, and QR code access. | FR-3c |
| **R-11** | Mechanisms for data backup and recovery must be implemented. | FR-3e |
| **R-12** | Data access speed must not exceed 10 seconds. | NFR-1 |
| **R-13** | The system must operate through a single, unified interface. | NFR-2 |
| **R-14** | The system must ensure data confidentiality, integrity, and access control. | NFR-3 |
| **R-15** | The system must be stable, dependable, and versatile (Reliability). | NFR-5 |
| **R-16** | The GUI should offer multiple language support. | FR-3f |
| **R-17** | The GUI should offer multiple color theme options. | FR-3g |
