[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

### Introduction

The filenames of Minimap textures stored in MPQ Archives are hashed using MD5. The TRS file provides an easy lookup from real pathnames like `Azeroth\map00_00.blp` to the corresponding hashed filename `f16354735dad4e22e175a398a01992ba.blp`

### File Structure

TRS is a plain human-readable text file. Every directory is started by a line that looks like

    dir: Azeroth

after which a table with two columns (tab-separated) lists the corresponding clear-text filenames and hash filenames like this:

    Azeroth\map00_00.blp    f16354735dad4e22e175a398a01992ba.blp
    Azeroth\map00_01.blp    3f6b258da2fe615b620d34eaa26bb0cc.blp
    Azeroth\map00_02.blp    6e2e4a333dc88a8581c727d3207d04f8.blp
    Azeroth\map01_00.blp    1c415ef6183e799c137c959596e34c40.blp
    Azeroth\map01_01.blp    8abbe680628429c4c6e6abf286bfed68.blp
    Azeroth\map01_02.blp    018be401f83b315df7abc887324cc1e2.blp
    ...
