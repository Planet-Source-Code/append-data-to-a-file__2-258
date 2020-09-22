<div align="center">

## Append data to a file


</div>

### Description

In Java 1.1 you can just pass true as the second argument to this FileOutputStream constructor to indicate that you want to append data to the file:

public FileOutputStream(String name, boolean append)

throws IOException

In Java 1.0, however, you must use the java.io.RandomAccessFile class that lets you read and write bytes from arbitrary locations in a file. This class implements DataInput and DataOutput so you have all the methods of DataInputStream and DataOutputStream available to you.

To create a new random access file pass the name of the file and the mode to the constructor. The mode is either "r" (read-only) or "rw" (read and write). The length() method returns a long that tells you how many bytes there are in a file and the seek(long p) method lets you position the file pointer at a particular point in the file. Thus to start writing at the end of a RandomAccessFile raf, you first raf.seek(raf.length()). The following example demonstrates by appending the string "Kilroy was here!" to every file specified on the command line.

(Java FAQ:found on the web at:http://sunsite.unc.edu/javafaq/javafaq.html)
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[N/A](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/empty.md)
**Level**          |Unknown
**User Rating**    |4.7 (28 globes from 6 users)
**Compatibility**  |Java \(JDK 1\.1\)
**Category**       |[Input/ Output](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/input-output__2-84.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/append-data-to-a-file__2-258/archive/master.zip)





### Source Code

```
import java.io.*;
class AppendToAFile {
 public static void main (String args[]) {
  for (int i = 0; i < args.length; i++) {
   //First open the file you want to append to
   try {
    RandomAccessFile raf = new RandomAccessFile(args[i], "rw");
    // Position yourself at the end of the file
    raf.seek(raf.length());
    // Write the String into the file. Note that you must
    // explicitly handle line breaks.
    raf.writeBytes("\nKilroy was here!\n");
   }
   catch (IOException e) {
    System.out.println("Error opening file: " + e);
   }
  }
 }
}
```

