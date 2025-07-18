# Forensic-Task
  Conducted a forensic investigation on a provided image as well as a file with a hash, this was to confirm the integrity of the evidence. The first step of the                investigation is the planning of the investigation.
  **This report is a summerized version**
  
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


# Investigation

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

**Provided Hash info**

![Image of Checksum and more](fig8.png)

**Hash Calculation**

![Hash Calculation Image](fig9.png) 

The hash calculated is the same as the hash provided, thus the integrity of the image is valid.

Used WinHex to check the partition tables of the image
**Partition Table** 

![Image of Partition Table](fig10.png)

Checked the partition table from 0x1BE and copied the result to a notepad. The image below describes the partitions. 

![notes of partition table](fig11.png)

The two table images below helped understanding the volume/size and file type of each partition.

![table1](tb1.png)
![table2](tb2.png)


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

Clue.txt was put through hashes.com (an online cracking website). The result is displayed in the image below.

![cracked hash image](Fig21.png)

The rest of the files were investigated and logged, though most did not have any meaningful data. Using another recovery key found within the F volume, volume G was unlocked.

**Accessing Volume G (3/4)**
Similar to Volume F, Volume G had no data or hidden files. Running this volume through r-studio did recover data that could be investigated.  

Files recovered from Volume G from (file 1/2 named root); (Refer to images below)
•	$RECYCLE.BIN
  o	Desktop file
•	1. Welcome to Windows Forensic Analysis
  o	5 videos
•	2. The Donald Blake Case
  o	8 videos
•	Keys (was an empty folder)
•	System Volume Information (around 18 files and 2 folders)
  o	$LIENT (Empty folder)
  o	AadRecoverPasswordDelete
    -	1 txt file containing a recovery key.

![Recovered Volume G](Fig26.png)
![Recovered Volume G](Fig27.png)

All Data within these files were logged seperately. A few recovery passwords were found and applied to the leftover Volume H;

**Accessing Voume H**
Volume H had two text documents 
1. Registry
2. Test

The test file had no useful data thus the registry file was accessed.
The data recovered from this file included the following;
•	Active computer name - Fig39
•	Product name - Fig40
•	Product ID - Fig41
•	Installed Date and Time 
•	Registered Owner - Fig42
•	Time Zone Key Name - Fig40
•	Network Cards - Fig43
•	Friendly names of USB connected - Fig44, Fig45, Fig46, Fig47, Fig48

![alt text](Fig39.png)
![alt text](Fig40.png)
![alt text](Fig41.png)
![alt text](Fig42.png)
![alt text](Fig43.png)
![alt text](Fig44.png)
![alt text](Fig45.png)
![alt text](Fig46.png)
![alt text](Fig47.png)
![alt text](Fig48.png)

**Summary of Data collected**

![data collected](Tb3.png)

# End Notes
There are many forensics guidelines that are in place for specific reasons such as safety, integrity and security. Many organizations have their own guidelines to prevent any breach of privacy or forms of tampering of evidence by unauthorized individuals.

It is recommended to have evidence/device delivered to by a secondary source, it is best to consider that tampering can occur through that source, and thus it is better to send trusted personnel to handle the evidence along with the time stamps, signature and possibly location (i.e. maintain a chain of custody).

The device should be stored securely in a location with physical and virtual security, this may be a room with locks that is remotely monitored and controlled in terms of temperature, and humidity. The handlers should also be trained so as to not expose the physical evidence to any magnetic fields or static current. The evidence should also be handled in pairs.

The evidence should be maintained as an image and have regular and remote backup, and the investigators should document as they conduct the investigation.

The investigation should only occur within the lab, and should only be conducted on the organizational workstations and tools (so there is no way to steal data). The lab should also be monitored by cameras; no personnel should be allowed to take any technological device to the lab.

Training and reviews should be conducted along with tests to ensure that the technical staff are all up to standards. This way the staff can be reminded of legal and ethical restrictions that may compromise their work or investigation.

This concludes the end of the recommendations regarding the improvement of the process and procedures in the method of conducting digital forensics.

