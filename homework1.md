0. Assess learned path name expansion construction. Provide an example of how to quickly rename `filename.tot` to `filename.txt`

 mv filename.tot filename.txt
 find . -name '*.tot' -exec sh -c 'mv "$0" "${0%.tot}.txt"' {} \;
 
0. Write a one-liner that will result with a message "Was found!" if grep found an occurence of pattern and "Wasnt' found..." and add pattern as a last line of file if not. Should start like: `grep <pattern> <filename> ...`. Use variables to avoid duplication of pattern
0. Write out as much as possible ways to go from `/usr/share` folder to `/home/centos/.ssh`

 азличные относительные пути также считаются разными вариантами 
 1 путь сразу:
 [lode00@localhost mnt]$ cd /home/centos/.ssh
 2 такой: [lode00@localhost mnt]$ cd .. 
 [lode00@localhost /]$ cd home 
 [lode00@localhost home]$ cd lode00 
 3 вариант: [lode00@localhost mnt]$ cd 4 вариант [lode00@localhost mnt]$ cd ~


0. Write a pipe that will result with a unique list of commands/shells from /etc/passwd file (last column of it)
 
 cut -d: -f7 /etc/passwd

0. In `/usr/bin` find all files which names consist only from letters and have length from 4 to 6. The result should be a list of files
0. Find all man pages that contain word `malloc`. The result should be just a list of files
  [lode00@localhost home]$ find /usr/share/man | grep -E 'malloc'

0. Awk. Count how much entries there are in /var/log/messages for each program (kernel, systemd, etc.). Output should look like:
```
systemd: 145
kernel: 23
...
```
0. Sed and regular expressions. Stacktraces of JVM languages looks the following way:
```
 at com.databricks.backend.daemon.data.client.DatabricksFileSystemV2.recordOperation(DatabricksFileSystemV2.scala:474)
 at com.databricks.backend.daemon.data.client.DBFSV2.initialize(DatabricksFileSystemV2.scala:64)
 at com.databricks.backend.daemon.data.client.DatabricksFileSystem.initialize(DatabricksFileSystem.scala:222)
 at org.apache.hadoop.fs.FileSystem.createFileSystem(FileSystem.java:2669)
 at org.apache.hadoop.fs.FileSystem.access$200(FileSystem.java:94)
 at org.apache.hadoop.fs.FileSystem$Cache.getInternal(FileSystem.java:2703)
```
Write a sed one-liner that will show stack traces lines in the following fashion:
```
Exception occured inside method `org.apache.hadoop.fs.FileSystem$Cache.getInternal` from file `FileSystem.java` on line `2703`. The file was written in `java`.


Called method org.apache.hadoop.fs.FileSystem$Cache.getInternal which calls line 2703 of file FileSystem.java. The file is written in java.
```
NOTE: sed capture groups are extra useful here
