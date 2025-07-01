# Forensic-Task
  Conducted a forensic investigation on a provided image as well as a file with a hash, this was to confirm the integrity of the evidence. The first step of the                investigation is the planning of the investigation.

**Planning**
  •	It is important to document everything about the evidence and investigation such as (who will conduct the investigation, the expected outcome and what tools and              techniques will be used).
  •	The evidence should be allocated in a room with locks and surveillance cameras (to monitor who accesses the evidence).
  •	The new staff should be mentored and monitored.
  •	The tools/equipment must be correct and up to standards, and they should be tested regularly to ensure they produce correct results.
  •	Have a case management system (keeping track of the date, time and person handling the evidence with a unique reference number of evidence and court dates, etc.).
  •	Use write blockers
  •	Use imaging tools (that have specific requirements)

**Pre-investigation recomendations**
  •	Mark the date and time the evidence is handed over
  •	All staff who are investigating should meet specified standards
  •	Tools and techniques should be verified and examined to meet standards and ensure correct result
  •	Investigators should regularly review legal restrictions.
  •	The evidence collected should be stored in a secure and climate-controlled room.

# Disk Forensics Investigation  
**Goal**: Recover required data from a forensic image.
  •	Verify the image through the Hash provided.
  •	Access, analyze and document all the data within the files along with the steps taken (after accessing the first volume, it will contain the answer to access the next        volume and so on).
  •	Search for a registry within the image/volumes.
  •	Access the registry and conduct registry forensics.
  
  A registry is hidden within the files, the data gathered from said registery should be of the following;
  •	Active computer name
  •	Product name
  •	Product ID
  •	Network card (first connected and last connected)
  •	Names of USB connected
  •	Time zone of the device


**Investigation**
  **Identification**
    The evidence given was an image of a hard disk (1GB of data) along with its hash. I am required to conduct a digital forensics on an image of a hard disk and report all      the data found within it. The image is expected to contain multiple files hiding a lot of different data with one file containing a registry. 
  
  **Tools**: 
    •	WinHex (for checking partition tables)
    •	OS Forensics (for hash verification and any other task if necessary)
    •	R-Studio (for data recovery)
  
  **Planning**
  Planning the approach to the investigation is an essential part of a digital forensics investigation. thus my plan was as follows;
  The first step to starting the investigation will consist of verifying the Hash of the image, if the Hash provided matches with the Hash of the image then the integrity of   the evidence is valid and the investigation may continue. If the hash does not match, then the evidence has been tampered with and there is no point in continuing the        investigation.
  If the image hash matches the one provided, the next step will be checking the partition tables to gather information regarding the volumes and storage required. This also   will be documented and described below. The files within the image were be locked and one hint provided was the keyword “forensics”. 

