[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------
## Introduction

The following files follow a chunked structure: [ADT](Reference%20Information/Client%20Files/ADT.md), [WDT](Reference%20Information/Client%20Files/WDT.md), [WMO](Reference%20Information/Client%20Files/WMO.md) and [WDL](Reference%20Information/Client%20Files/WDL.md) they consist of chunks in the following format:

    Offset   Type            Description
    ----------------------------------------------------------------------
    00h      char[4]         Chunk identifier - in reverse character order
    04h      uint32          Chunk size
    08h      size*bytes      Chunk data

The initial chunk in all of these files is an MVER chunk, specifying the version of the files in a 32-bit integer.
All files use little-endian byte order.