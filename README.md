# QAAS: Quick Access Archive System
  Document indexing for companies and institutions.
  
<br>

# About QAAS
**QAAS** is a digital archiving solution that aims to modernize the documentation procedure in governmental institutions. 
We plan to leverage the **NFC Capability** in the governmental IDs to allow for instant file access. 

<br>

# Goals
**Saving valuable time** in governmental institutions by:
- Digitalizing the archiving process.
- Storing documents securely in a **local SQL database**.
- Using **NFC-enabled IDs** to grant officials direct access to citizens’ files.
- Minimizing queues and physical handling of documents.

<br>

# Tools and Development Enviroment
During the **development phase** we will be using the **[USBWebserver](https://github.com/grimgravy/USBWebServer)** software to create an intitial **Proof of Concept (POC)** for the project.

**Note on Licensing:** USBWebserver is distributed under the GNU General Public License (GPL) Version 2, which grants the freedom to use and run the software. Our project's code is an independent work that runs on this environment.

<br>

# File Structure
<br>
-> USBWebServer <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> \root : this is where all the project files reside <br>
    &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <I><B>(all the future web pages will be added in this folder)</B></I> <br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-> \images : folder holding the images to be used in the website <br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-> index.php : main page <br>
      &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;-> style.css : style sheet <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> \apache : server binaries and configurations <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> \mysql : internal database files <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> \php : php executables <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> \phpmyadmin : MySQL manager executable <br>
    &nbsp;&nbsp;&nbsp;&nbsp;-> settings.ini : stores the general settings <br>

<br>

# Status
**Implementation is soon to be started.** The project is currently in the planning and environment setup phase.

**Version**: N/A
