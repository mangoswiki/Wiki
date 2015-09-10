<style>
    .blackline
    {
        background-color: #d0d0d0;
        color: #black;
        font-family: arial, sans-serif;
        font-size: 16px;
        text-align: left;
        padding: 4px;
        border-top-left-radius: 10px 5px;
        padding-left: 10px;
        border-top-right-radius: 10px;
        -moz-border-radius-topleft: 10px 5px;
        -moz-border-radius-topright: 10px;
    }
    .blackborder
    {
        border-color: #000000;
        background-color: #444444;
        border-width: 2px;
        padding: 3px;
        border-style: solid;
        color: #FFFF66;
        font-family: arial, sans-serif;
        font-size: 14px;
        text-align: left;
    }
    .blueline
    {
        background-color: #0088FF;
        color: #FFFFFF;
        font-family: arial, sans-serif;
        font-size: 18px;
        text-align: center;
        padding: 4px;
        border-top-left-radius: 10px 5px;
        border-top-right-radius: 10px;
        -moz-border-radius-topleft: 10px 5px;
        -moz-border-radius-topright: 10px;
    }
    .blueborder
    {
        border-color: #0088FF;
        background-color: #BBDDFF;
        border-width: 2px;
        padding: 3px;
        border-style: solid;
        color: #000000;
        font-family: arial, sans-serif;
        font-size: 14px;
        text-align: left;
    }
    .greenline
    {
        background-color: #33BB44;
        color: #FFFFFF;
        font-family: arial, sans-serif;
        font-size: 18px;
        text-align: center;
        padding: 4px;
        border-top-left-radius: 10px 5px;
        border-top-right-radius: 10px;
        -moz-border-radius-topleft: 10px 5px;
        -moz-border-radius-topright: 10px;
    }
    .greenborder
    {
        border-color: #33BB44;
        background-color: #BBFFCC;
        border-width: 2px;
        padding: 3px;
        border-style: solid;
        color: #000000;
        font-family: arial, sans-serif;
        font-size: 14px;
        text-align: left;
    }
    .redline
    {
        background-color: #DD6644;
        color: #FFFFFF;
        font-family: arial, sans-serif;
        font-size: 18px;
        text-align: center;
        padding: 4px;
        border-top-left-radius: 10px 5px;
        border-top-right-radius: 10px;
        -moz-border-radius-topleft: 10px 5px;
        -moz-border-radius-topright: 10px;
    }
    .redborder
    {
        border-color: #DD6644;
        background-color: #FFCCBB;
        border-width: 2px;
        padding: 3px;
        border-style: solid;
        color: #000000;
        font-family: arial, sans-serif;
        font-size: 14px;
        text-align: left;
    }
    .yellowline
    {
        background-color: #DDDD44;
        color: #000000;
        font-family: arial, sans-serif;
        font-size: 18px;
        text-align: center;
        padding: 4px;
        border-top-left-radius: 10px 5px;
        border-top-right-radius: 10px;
        -moz-border-radius-topleft: 10px 5px;
        -moz-border-radius-topright: 10px;
    }
    .yellowborder
    {
        border-color: #DDDD44;
        background-color: #FFFFBB;
        border-width: 2px;
        padding: 3px;
        border-style: solid;
        color: #000000;
        font-family: arial, sans-serif;
        font-size: 14px;
        text-align: left;
    }
    .dosline
    {
        border-color: #C0C0C0;
        background-color: #444444;
        border-width: 0px;
        padding: 0px;
        border-style: solid;
        color: #FFFFFF;
        font-family: courier, sans-serif;
        font-size: 12px;
        text-align: left;
    }
    .doslinered
    {
        border-color: #C0C0C0;
        background-color: #444444;
        color: #FF9955;
        font-family: courier, sans-serif;
        font-size: 12px;
        text-align: left;
    }
    .doslineyellow
    {
        border-color: #C0C0C0;
        background-color: #444444;
        color: #FFFF88;
        font-family: courier, sans-serif;
        font-size: 12px;
        text-align: left;
    }

</style>
[![](/wiki/icons/home.gif)](/wiki/Home.md) 
[![](/wiki/icons/back.gif)](/wiki/Installation%20Guides/Installation%20Guides.md)

----------

##How to Obtain the MaNGOS sourcecode
 
<div class='blueline'>Important Things to remember</div>
<div class='blueborder'>There are Five MaNGOS cores, each designed to support a specific version of WOW<br/>
<table border='0' cellpadding=3 cellspacing=8 width='100%'>
<tr>
<td align=centre width='20%'><b>Core</b></td><td width='30%'><b>Supporting</b></td><td><b>Client Version</b></td>
</tr>
<tr>
<td align=centre>MangosZero</td><td>Vanilla</td><td>1.12.1(5875), 1.12.2(6005) & 1.12.3(6141).</td>
</tr>
<tr>
<td align=centre>MangosOne</td><td>The Burning Crusade</td><td>2.4.3(8606).</td>
</tr>
<tr>
<td align=centre>MangosTwo</td><td>Wrath of the Lich King</td><td>3.3.5a(12340).</td>
</tr>
<tr>
<td align=centre>MangosThree</td><td>Cataclysm</td><td>4.3.4 (Build 15595).</td>
</tr>
<tr>
<td align=centre>MangosFour</td><td>Mists of Pandaria</td><td>5.4.8 (Build 18414).</td>
</tr>
</table>
</div>
<div class='yellowborder'><b>NOTE: </b>The default branch of all the repos is always the latest released version, however between releases other branches contain the ongoing development work.</div>

###Cloning the default branch of the repos

<div class='blackline'><b>Server Source.</b> Type:</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git clone</span> <span class='doslinered'>https://gitub.com/mangoszero/server.git</span> <span class='doslineyellow'>--recursive</span></div><br />

<div class='blackline'><b>Database.</b> Type:</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git clone</span> <span class='doslinered'>https://gitub.com/mangoszero/database.git</span> <span class='doslineyellow'>--recursive</span></div><br />
The server and database folders then contain the contents of each repo.

###Cloning a specific branch of the repos

If you want the try out the latest development work in progress, they are available.

<div class='blackline'><b>Server Source.</b> Using branch develop21. Type:</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git clone</span> <span class='doslinered'>https://gitub.com/mangoszero/server.git</span> <span class='doslineyellow'>--recursive -b develop21</span></div><br />

<div class='blackline'><b>Database.</b> Using branch develop21. Type:</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git clone</span> <span class='doslinered'>https://gitub.com/mangoszero/database.git</span> <span class='doslineyellow'>--recursive -b develop21</span></div><br />
The server and database folders then contain the contents of each repo for this branch.
