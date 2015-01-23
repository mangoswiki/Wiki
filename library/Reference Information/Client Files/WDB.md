[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

### Header 

The header is of 16 bytes for pre-1.6 files, and 20 bytes for post-BC files: 

<table border="1" cellspacing='0' cellpadding='5' bgcolor='#f0f0f0'>
<tr bgcolor='#e0e0e0'><td align="center" valign="middle"><b>FieldName</b></td><td align="center" valign="middle"><b>Length</b></td><td align="left" valign="middle"><b>Description</b></td></tr>

<tr><td align="center" valign="middle">Signature</td><td align="center" valign="middle">4-bytes char</td><td align="left" valign="middle">File Signature</td></tr>

<tr><td align="center" valign="middle">Build</td><td align="center" valign="middle">4-bytes int</td><td align="left" valign="middle">Build Identifier</td></tr>

<tr><td align="center" valign="middle">Locale</td><td align="center" valign="middle">4-bytes char</td><td align="left" valign="middle">Locale Identifier, reversed (ie. SUne for enUS)</td></tr>

<tr><td align="center" valign="middle">Unknown</td><td align="center" valign="middle">4-bytes int</td><td align="left" valign="middle">Added in 1.6 (May be first compatible client build for this db version. not  verified)</td></tr>

<tr><td align="center" valign="middle">Unknown</td><td align="center" valign="middle">4-bytes int</td><td align="left" valign="middle">Added in 1.6 (Region code. not  verified)</td></tr>

<tr><td align="center" valign="middle">Unknown</td><td align="center" valign="middle">4-bytes int</td><td align="left" valign="middle">Added in 3.0.8.9464, always null</td></tr>

</table>

### Signatures 
Signatures, just like locales, are reversed in the header. 

<table border="1" cellspacing='0' cellpadding='5' bgcolor='#f0f0f0'>
<tr bgcolor='#e0e0e0'><td align="center" valign="middle"><b>Signature</b></td><td align="center" valign="middle"><b>Filename</b></td><td align="left" valign="middle"><b>Description</b></td></tr>

<tr><td align="center" valign="middle">BDIW</td><td align="center" valign="middle">Itemcache.wdb</td><td align="left" valign="middle">Warcraft Item Database</td></tr>

<tr><td align="center" valign="middle">BDNW</td><td align="center" valign="middle">Itemnamecache.wdb</td><td align="left" valign="middle">Warcraft Item Name Database</td></tr>

<tr><td align="center" valign="middle">BOGW</td><td align="center" valign="middle">Gameobjectcache.wdb</td><td align="left" valign="middle">Warcraft Game Object Database</td></tr>

<tr><td align="center" valign="middle">BOMW</td><td align="center" valign="middle">Creaturecache.wdb</td><td align="left" valign="middle">Warcraft MOB Database</td></tr>

<tr><td align="center" valign="middle">CPNW</td><td align="center" valign="middle">Npccache.wdb</td><td align="left" valign="middle">Warcraft NPC Database</td></tr>

<tr><td align="center" valign="middle">NDRW</td><td align="center" valign="middle">Wowcache.wdb</td><td align="left" valign="middle">Warden Cache</td></tr>

<tr><td align="center" valign="middle">TSQW</td><td align="center" valign="middle">Questcache.wdb</td><td align="left" valign="middle">Warcraft Quest Database</td></tr>

<tr><td align="center" valign="middle">XTIW</td><td align="center" valign="middle">Itemtextcache.wdb</td><td align="left" valign="middle">Warcraft Item Text Database</td></tr>

<tr><td align="center" valign="middle">BDPW</td><td align="center" valign="middle">Pagetextcache.wdb</td><td align="left" valign="middle">Warcraft Page Text Database</td></tr>

</table>

### EntryLength 

The EntryLength is the length in bytes of the cached row. It is always found in the second column and helps the game determinate corrupted cache entries as well as optimizing the reading process. 
Rows with an incorrect EntryLength are cleared on log in.
 
### EOF (End Of File) 

All WDB files end with 8 times \x00
