# Use Cases

# Key Actors

  **1. Civilian:** <br>
                   - Provides the NFC card 
                   
  **2. Official:** <br>
                   - Scans the NFC card to request the data from the database <br>
                   - Receives and views the data related to the civilian <br>
                   - Updates the civilians documents if necessary (all updates are later validated by the archive manager) <br>

  **3. Archiver:** <br>
                   - Uploads files <br>
                   - Validates data and changes <br>
                   - Views data <br>
                   - Updates documents if necessary <br>
                   
  **4. Administrator:** <br>
                   - Manages user accounts <br>
                   - Periodically cleans up the database logs and temp files <br>
                   - Pulls access logs and change records <br>
                   - Monitors system performance records <br>
                   - Backs up the database <br>
<br>

# Detailed Descriptions 

**1. Civilian -> [provide NFC]:** <br>
    - Starts when: NFC ID is presented by the civilian <br>
    - Ends when: NFC ID tag is scanned <br>

  Providing the NFC ID card is the first step of the data fetching process, the NFC ID is then used by the official to access the required documents related to this civilian <br>

**2. Official -> [Requests data]:** <br>
    - Starts when: Official scans the NFC tag on their NFC scanner <br>
    - Ends when: List of documents is returned by the system and displayed on the official's screen <br>

  Requesting the data is the key aspect of the project, each ID tag is used to index the respective civilian's documents <br>

**3. Archiver -> [Uploads files]:** <br>
    - Starts when: Archiver scans/uploads documents to an NFC index  <br>
    - Ends when: System confirms the documents are saved and to the correct index <br>

  Uploading files requires the archiver to upload the documents with an NFC tag to index it, this is a 1 time process that will eliminate the need to frequently revisit the archive <br>

**4. Adminstrator -> [Database cleanup]:** <br>
    - Starts when: Adminstrator manually or automatically clears irrelevant queries and temporary files <br>
    - Ends when: System confirms memory refresh and cleanup routine are complete <br>

  Regularly maintaining the database allows it to be more reliable and perform better, this task is the responsibility of the adminstrator. 
<br>

# Use-case diagram

![USE-CASE-DIAGRAM](<assets/usecase-diagram.jpg>)
