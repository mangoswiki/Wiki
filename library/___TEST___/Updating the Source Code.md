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

##How to Update your local repos
 
<div class='blackline'>Change directory to your Server Source folder, then type</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git pull </span> <span class='doslinered'>--recurse-submodules</span></div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git submodule </span> <span class='doslinered'>init</span></div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git submodule </span> <span class='doslinered'>update</span></div><br />

<div class='blackline'>Change directory to your Database Source folder, then type</div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git pull </span> <span class='doslinered'>--recurse-submodules</span></div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git submodule </span> <span class='doslinered'>init</span></div>
<div class='dosline'><span class='doslineyellow'>&nbsp;&nbsp;git submodule </span> <span class='doslinered'>update</span></div><br />

The server and database folders will then contain the updated contents of each repo for this branch.
