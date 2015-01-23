[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md) 

----------
## How to Update?
### Updating MaNGOS source
First off you should have git installed. Then you can `cd` into your mangos source folder. For example: `cd /c/MaNGOS/` When you are inside of there you type `git pull`.
 
### Updating database
After updating MaNGOS you might need to update the database structure.

 To find out, simply start MaNGOS and see if it gives you a "database error". 
 If it does you must apply all updates from the sql update folder which is "after" what update mangos tells you you currently have. 
 
 Note that you should apply the updates on the correct databases (See filenames in updates folder)

### Updating Scripts
As with updating MaNGOS you must `cd` into the git repository, for example `cd /c/MaNGOS/src/bindings/ScriptDev2`. Then you type `git pull`.

**Note:** 
After both the MaNGOS and Scripts update procedure you must recompile the core.

The reason we do this in mangos is to see if there are any database updates, then you will want the latest PvE "scripting" from the Scripts Library on top of the core updates for extra functionality and playability.

