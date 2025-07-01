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

**Execution**
I used the software OS forensics and used the verify/create hash tool. After selecting the file button and entering the file path of the image, I selected the types of hash functions needed (these were SHA-1 and SHA-256).
In the comparison hash, I added the hash provided from the ‘image info’ file that contained the SHA-1 and SHA-256 hash. I used the SHA-256 hash and selected the calculate option so the software would calculate and verify automatically.
Provided Hash info(FIG8)
Hash calculation (FIG9)
The hash calculated is the same as the hash provided, thus the integrity of the image is valid.

Used WinHex to check the partition tables of the image
Partition Table (FIG10)
checked the partition table from 0x1BE and copied the result to a notepad. The image below describes the partitions. (FIG11)
The two table images below helped understanding the volume/size and file type of each partition.
(TB1 + TB2)

**Accessing the Image itself**
Directly accessing the files was not possible, because an error would show up stating that the disc was corrupted. To counter this error, I created a virtual hard disc (VHD) and partitioned it according to the file types and size.

**Accessing Volume E (1/4)**
All the Volumes were locked via a bitlocker. Volume E was the only volume that was unlocked using the hint (password being forensics).
There were a few hidden files in total (2 files and 2 folders); one was an mp4, one was a png and two folders. 
The png file was initially hidden and would not open so I copied it and applied a few different file extensions to check if some data would be retrieved (the pdf extension was successful). The data found was mostly junk or misleading within this volume save for a bitlocker recovery key which was applied to the other 3 volumes (Volume F was unlocked).

**Accessing Volume F (2/4)**
The result of accessing Volume F displayed nothing (i.e. it was empty).
After recovering the data within the volume by running it through R-Studio, the result displayed two files (Root and metafiles).

The “Root” folder contained 6 files and one folder.
•	3 files were mp4 files
•	3 files were txt files, 2 of them were empty and the last “clue.txt” contained a hash.
•	The last folder was named “Keys”
