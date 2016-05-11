# Forensics

## Initial exploration (initial identification)
* strings - Allows you to search and extract ASCII strings from a binary. Search for common encodings of the flag
  header.
* file - To try to identify the file type
* wireshark - Analyze the traffic, export interesting objects, search anomalies

## Data carving - Tools that search a file and extract identified files
* [foremost] (http://foremost.sourceforge.net/)
* [hachoir] (https://bitbucket.org/haypo/hachoir/wiki/Home)
* [binwalk] (http://binwalk.org/) - Pretty famous flexible data carver with entropy analysis
* [netwotkminer] (http://www.netresec.com/?page=NetworkMiner) - Carving for PCAP files
* [photorec] (http://www.cgsecurity.org/wiki/PhotoRec) Specific carver for images

## Memory dumps inspection
* [Volatility] (https://github.com/volatilityfoundation/volatility) - Memory extraction utility
* gdb - Core dump analysis

## Filesystems inspection
 * fdisk - Inspect disk image
 * testdisk - Find lost partitions
