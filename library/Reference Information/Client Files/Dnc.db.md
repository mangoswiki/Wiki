[![](/wiki/icons/home.gif)](/wiki/Home.md)

----------

## Introduction

dnc.db specifies the day-night cycle. It hasn't changed in any way from 1.0 or even 0.*. This looks like info for outdoor lighting with respect to the day-night cycle. The colors for the differnt light types are self-explanatory. The XYZ coordinates specify a directional light source.

## Header
8 bytes at the beginning of the file specify the number of rows (including head row) and columns

    00h    uint32 	Number of Rows
    04h    uint32  	Number of Columns

## Data

Each data field has exactly 8 bytes. 

    00h    uint32 	Field Type (0x53=S for String, 0x46=F for Float)
    04h    uint32  	Field Value

String value types are offsets into a Block of Zero-Terminated strings at the end of the file.

## File contents

Extracted and Formatted for a better overview.

<table>
<tr><th>Hour </th><th>Minute </th><th>DayIntensity </th><th>DayR </th><th>DayG </th><th>DayB </th><th>DayX </th><th>DayY </th><th>DayZ </th></tr>
<tr><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.0</td><td>1.0</td></tr>
<tr><td>1.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.3</td><td>1.0</td></tr>
<tr><td>2.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.5</td><td>0.9</td></tr>
<tr><td>3.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.7</td><td>0.7</td></tr>
<tr><td>4.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.9</td><td>0.5</td></tr>
<tr><td>5.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-1.0</td><td>0.3</td></tr>
<tr><td>6.0</td><td>0.0</td><td>0.8</td><td>0.5</td><td>0.5</td><td>0.5</td><td>0.7</td><td>-1.0</td><td>0.0</td></tr>
<tr><td>7.0</td><td>0.0</td><td>0.8</td><td>0.5</td><td>0.5</td><td>0.5</td><td>0.7</td><td>-1.0</td><td>-0.3</td></tr>
<tr><td>8.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.6</td><td>0.7</td><td>-0.9</td><td>-0.5</td></tr>
<tr><td>9.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.6</td><td>0.7</td><td>-0.7</td><td>-0.7</td></tr>
<tr><td>10.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>-0.5</td><td>-0.9</td></tr>
<tr><td>11.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>-0.3</td><td>-1.0</td></tr>
<tr><td>12.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.0</td><td>-1.0</td></tr>
<tr><td>13.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.3</td><td>-1.0</td></tr>
<tr><td>14.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.5</td><td>-0.9</td></tr>
<tr><td>15.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.7</td><td>-0.7</td></tr>
<tr><td>16.0</td><td>0.0</td><td>0.8</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.7</td><td>0.9</td><td>-0.5</td></tr>
<tr><td>17.0</td><td>0.0</td><td>0.8</td><td>0.8</td><td>0.5</td><td>0.5</td><td>0.7</td><td>1.0</td><td>-0.3</td></tr>
<tr><td>18.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.3</td><td>0.3</td><td>0.7</td><td>1.0</td><td>0.0</td></tr>
<tr><td>19.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.1</td><td>0.1</td><td>0.7</td><td>1.0</td><td>0.3</td></tr>
<tr><td>20.0</td><td>0.0</td><td>0.0</td><td>0.2</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.9</td><td>0.5</td></tr>
<tr><td>21.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.7</td><td>0.7</td></tr>
<tr><td>22.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.5</td><td>0.9</td></tr>
<tr><td>23.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.3</td><td>1.0</td></tr>
</table>
<table>
<tr><th>Hour </th><th>Minute </th><th>NightIntensity </th><th>NightR </th><th>NightG </th><th>NightB </th><th>NightX </th><th>NightY </th><th>NightZ </th></tr>
<tr><td>0.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>0.0</td><td>-1.0</td></tr>
<tr><td>1.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>0.3</td><td>-1.0</td></tr>
<tr><td>2.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>0.5</td><td>-0.9</td></tr>
<tr><td>3.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>0.7</td><td>-0.7</td></tr>
<tr><td>4.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>0.9</td><td>-0.5</td></tr>
<tr><td>5.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>1.0</td><td>-0.3</td></tr>
<tr><td>6.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>1.0</td><td>0.0</td></tr>
<tr><td>7.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>1.0</td><td>0.3</td></tr>
<tr><td>8.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.9</td><td>0.5</td></tr>
<tr><td>9.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.7</td><td>0.7</td></tr>
<tr><td>10.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.5</td><td>0.9</td></tr>
<tr><td>11.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.3</td><td>1.0</td></tr>
<tr><td>12.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>0.0</td><td>1.0</td></tr>
<tr><td>13.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.3</td><td>1.0</td></tr>
<tr><td>14.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.5</td><td>0.9</td></tr>
<tr><td>15.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.7</td><td>0.7</td></tr>
<tr><td>16.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.9</td><td>0.5</td></tr>
<tr><td>17.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-1.0</td><td>0.3</td></tr>
<tr><td>18.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-1.0</td><td>0.0</td></tr>
<tr><td>19.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-1.0</td><td>-0.3</td></tr>
<tr><td>20.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.0</td><td>0.7</td><td>-0.9</td><td>-0.5</td></tr>
<tr><td>21.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>-0.7</td><td>-0.7</td></tr>
<tr><td>22.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>-0.5</td><td>-0.9</td></tr>
<tr><td>23.0</td><td>0.0</td><td>1.0</td><td>0.0</td><td>0.0</td><td>0.5</td><td>0.7</td><td>-0.3</td><td>-1.0</td></tr>
</table>
<table>
<tr><th>Hour </th><th>Minute </th><th>Ambient<br>Intensity </th><th>AmbientR </th><th>AmbientG </th><th>AmbientB </th><th>FogDepth </th><th>FogIntensity </th><th>FogR </th><th>FogG </th><th>FogB </th></tr>
<tr><td>0.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.3</td><td>0.6</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>1.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.3</td><td>0.6</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>2.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.3</td><td>0.6</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>3.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.4</td><td>0.6</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>4.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.4</td><td>0.7</td><td>3700.0</td><td>0.7</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>5.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.4</td><td>0.7</td><td>3700.0</td><td>0.7</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>6.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.8</td><td>3700.0</td><td>0.7</td><td>0.1</td><td>0.1</td><td>0.1</td></tr>
<tr><td>7.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.8</td><td>3700.0</td><td>0.5</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>8.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.8</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>9.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>10.0</td><td>0.0</td><td>0.8</td><td>0.8</td><td>0.8</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>11.0</td><td>0.0</td><td>0.8</td><td>0.9</td><td>0.9</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>12.0</td><td>0.0</td><td>0.8</td><td>1.0</td><td>1.0</td><td>1.0</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>13.0</td><td>0.0</td><td>0.8</td><td>0.9</td><td>0.9</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>14.0</td><td>0.0</td><td>0.8</td><td>0.8</td><td>0.8</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.2</td><td>0.2</td><td>0.2</td></tr>
<tr><td>15.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.1</td><td>0.1</td><td>0.1</td></tr>
<tr><td>16.0</td><td>0.0</td><td>0.8</td><td>0.7</td><td>0.7</td><td>0.9</td><td>3700.0</td><td>0.3</td><td>0.1</td><td>0.1</td><td>0.1</td></tr>
<tr><td>17.0</td><td>0.0</td><td>0.8</td><td>0.6</td><td>0.6</td><td>0.8</td><td>3700.0</td><td>0.3</td><td>0.1</td><td>0.1</td><td>0.1</td></tr>
<tr><td>18.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.4</td><td>0.8</td><td>3700.0</td><td>0.5</td><td>0.1</td><td>0.1</td><td>0.1</td></tr>
<tr><td>19.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.4</td><td>0.7</td><td>3700.0</td><td>0.7</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>20.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.4</td><td>0.7</td><td>3700.0</td><td>0.7</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>21.0</td><td>0.0</td><td>0.8</td><td>0.4</td><td>0.3</td><td>0.7</td><td>3700.0</td><td>0.7</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>22.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.3</td><td>0.7</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
<tr><td>23.0</td><td>0.0</td><td>0.8</td><td>0.3</td><td>0.3</td><td>0.6</td><td>3700.0</td><td>0.8</td><td>0.0</td><td>0.0</td><td>0.1</td></tr>
</table>
