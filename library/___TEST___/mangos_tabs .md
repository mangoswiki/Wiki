    <style>
        .conts {
            visibility:hidden;
        }
        .tab {
            border-top: 1px solid #E0E0E0;
            border-right: 1px solid gray;
            border-left: 1px solid #E0E0E0;
            font-family:Verdana, sans-serif;
            font-size:10pt;
            text-align:center;
            font-weight:normal;
        }

        .selTab	{
            border-left: 1px solid #E0E0E0;
            border-top: 1px solid #E0E0E0;
            border-right: 1px solid black;
            font-weight:bold;
            text-align:center;
        }

    </style>
    <script language="javascript">
        function public_Labels(label1, label2, label3)
        {

            t1.innerText = label1;
            t2.innerText = label2;
            t3.innerText = label3;
        }

        function public_Contents(contents1, contents2, contents3)
        {

            t1Contents.innerHTML = contents1;
            t2Contents.innerHTML = contents2;
            t3Contents.innerHTML = contents3;
            init();
        }

        function init()
        {
            tabContents.innerHTML = t1Contents.innerHTML;
        }

        var currentTab;
        var tabBase;
        var firstFlag = true;


        function changeTabs()
        {

            if(firstFlag == true)
            {
                currentTab = t1;
                tabBase = t1base;
                firstFlag = false;
            }

            if(window.event.srcElement.className == "tab")
            {
                currentTab.className = "tab";
                tabBase.style.backgroundColor = "white";
                currentTab = window.event.srcElement;
                tabBaseID = currentTab.id + "base";
                tabContentID = currentTab.id + "Contents";
                tabBase = document.all(tabBaseID);
                tabContent = document.all(tabContentID);
                currentTab.className = "selTab";
                tabBase.style.backgroundColor = "";
                tabContents.innerHTML = tabContent.innerHTML;
            }
        }

    </script>
<body bgcolor="#FFFFFF" onclick="changeTabs()" onload="init()">
<div style="top:40px; height:100%; width:100%; left:25px; border:none thin gray">


    <table style="width:100%; height:250px" cellpadding="0" cellspacing="0">
        <tr>
            <td id="t1" class="selTab" height="25">First Tab</td>
            <td id="t2" class="tab">Second Tab</td>
            <td id="t3" class="tab">Antz Tab</td>
        </tr>
        <tr>
            <td id="t1base" style="height:2px; border-left:1px solid #E0E0E0"></td>
            <td id="t2base" style="height:2px; background-color:white"></td>
            <td id="t3base" style="height:2px; background-color:white; border-right:1px solid #E0E0E0"></td>
        </tr>
        <tr>
            <td height="*" colspan="7" id="tabContents" style="border-left:1px solid #E0E0E0; border-bottom:1px solid #E0E0E0; border-right:1px solid #E0E0E0">sample contents</td>
        </tr>
    </table>
</div>
<div class="conts" id="t1Contents">Tab 1 content</div>
<div class="conts" id="t2Contents">Tab 2 content</div>
<div class="conts" id="t3Contents">Antz content</div>
</body>
