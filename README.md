# BatchDateTime
How to get the Date and Time in a Batch for Windows

This is not a final, but just to get an idea how to set up a batch file for creating a auto ZIP system etc

Depending on OS Date System (just Examples):

1. US Date Format: MM|DD|YYYY is 12/24/2024

2. European format (UK and Germany): DD|MM|YYYY is 24/12/2024 or 24.12.2024

"|" ist just a placeholder seperator character in this examples!

Example:

```
set DATE=%date%
set TIME=%time%

set YYYY=%date:~6,4%
set MM=%date:~3,2%
set DD=%date:~0,2%

set HOU=%time:~3,2%
set MIN=%time:~3,2%
set SEC=%time:~6,2%
set MSEC=%time:~9,2%

set SUBFILENAME=%YYYY%-%MM%-%DD%

set SUBFILENAME=%YYYY%-%MM%-%DD%-%HOU%-%MIN%-%SEC%-%MSEC%

echo %DATE% %TIME%
echo %date% %time%

set SOURCEPATH="D:\FOLDER\Subdirectory"
set TARGETPATH="D:\FOLDER\Filename_%SUBFILENAME%.zip"

powershell.exe Compress-Archive -Path '%SOURCEPATH%' -DestinationPath '%TARGETPATH%'

REM Copy file with Powershell

set TARGETPATHNEW="D:\FOLDER\Filename.zip"

powershell.exe Copy-Item '%TARGETPATH%' -Destination '%TARGETPATHNEW%'

```

For C-Sharp option see also Custom date and time format strings
https://learn.microsoft.com/en-us/dotnet/standard/base-types/custom-date-and-time-format-strings

```
DateTime thisDate1 = new DateTime(2024, 12, 24);
DateTime thisDate1 = DateTime.Now; // Date now
Console.WriteLine("Today is " + thisDate1.ToString("MMMM dd, yyyy") + ".");

DateTimeOffset thisDate2 = new DateTimeOffset(2011, 6, 10, 15, 24, 16,
                                              TimeSpan.Zero);
Console.WriteLine("The current date and time: {0:MM/dd/yy H:mm:ss zzz}",
                   thisDate2);
// The example displays the following output:
//    Today is June 10, 2011.
//    The current date and time: 06/10/11 15:24:16 +00:00
```

