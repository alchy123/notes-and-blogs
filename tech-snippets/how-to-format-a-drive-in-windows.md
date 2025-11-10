## How to format a drive in Windows?

* [Click here to go one back](./readme.md).

* Check and find the disk number of your disk with ‘Get-Disk’ command
* This command clears the data of the disk you chosen. ‘Get-Disk {enter your disk number here, correctly} | Clear-Disk -RemoveData -RemoveOEM’
    * Example: “Get-Disk 2 | Clear-Disk -RemoveData -RemoveOEM”
    * **OEM partition** is designed for system recovery or factory restore. It allows users to easily and quickly restore the system to the original state when system failure or system crash occurs. This partition usually comes with Dell, Lenovo, or HP computers. ‘-RemoveOEM’ flag is removing also the OEM partition of your drive, otherwise it might throw an error. I don’t know how and why but my flash drive was having an OEM partition. I did use balena etcher for an ubuntu iso, maybe that was the reason, idk. Normally operating systems has OEM partitions and they OEM partitions comes with installing operating systems if I’m not mistaken.
* This command create a raw partition with the maximum empty space to the disk you choose and assigns a drive letter automatically ‘New-Partition -DiskNumber {enter your disk number here, correctly} -UseMaximumSize -AssignDriveLetter’
* Look at your drive letter from your previous command output or use ‘Get-Partititon’ command and look at your disk’s created new space’s letter.
* This command is formatting the volume to NTFS file system, giving a drive letter we specified, ‘Format-Volume -DriveLetter E -FileSystem NTFS -NewFileSystemLabel "Kingston64FlashDrive" -Confirm:$false’
* I did this formatting in windows but I also want to do this on linux in another time and take notes about that too.
* Some useful resources around this topic:
    * (https://www.cryer.co.uk/brian/windows/how_to_delete_an_oem_partition.htm) → a method I didn’t used in this personal documentation of mine.
    * (https://stackoverflow.com/questions/48048588/what-is-the-logic-behind-flags-and-methods#answer-48049563) -> about powershell cli logic