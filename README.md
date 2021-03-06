

<p align="center">
  <img src="https://github.com/KabueMurage/CL-QuickTranslate/blob/master/src/img/logo.jpeg?raw=true" alt=""/>
</p>

  # CL-QuickTranslate
  
  
 <img src="https://github.com/KabueMurage/CL-QuickTranslate/blob/master/src/img/logo.jpg?raw=true" align="left" alt="">
  
  
  *As present, you may have noticed that the Web version of Google Translate opens with standard European language pairs by default
  (none of which you may EVER use) , neither nowhere in the [Languages menu](https://translate.google.com) is there the possibility to set default
  pair languages for translation , nor are the last used pairs synced to your account, which leaves you with the boring alternative to navigate and select
  them from the drop-down menu or bookmark their [syntax appended url](https://translate.google.com/?langpair=en%7sw) for quick future use , and as a frequent user it might be a bit more painful to keep changing them.*
  
 
  To save time, you can use one liners from your commandline interface or fully automate file translations using batch scrips or any desired scripting  language.<br>
  

  ### Installation
  Download and add to [path](https://en.wikipedia.org/wiki/PATH_%28variable%29).  Running ``Qtranslate.exe -v`` should print the current version number.

### Syntax and Usage:
 
 |Parameter|Function|Default value|
 |--|--|--|
 |-s| Sets a text input. Text containing white spaces should be enclosed in double-quotes.|`Null`|
 |-l|Sets the destination language using a specified [ISO prefix](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwixuKmY9_LrAhVFCxoKHUgsB1kQFjAAegQIAxAB&url=https://cloud.google.com/translate/docs/languages&usg=AOvVaw0DS2aRvqlazR86JXJI1fsn) or a language identifier for Fun Translations (**yoda , valspeak, shakespeare jive cockney , brooklyn, ermahgerd or minion**). <br> The Source language is will be auto detected. |`None` <br> The identifier **must** be specified. |
 |-o| Specifies the path and name of the translated file to export a translation. The translated text is printed to the standard output by default. <br> Saving Prefixes :  <br> %l -  Language ISO Prefix.<br> %f - Filename.|A new file with a unique Random integer of filetype : `.txt`|
 | -f|Specifies the path and file name of the file to be translated. Long filenames should be enclosed in double-quotes. <br> *.txt*, *.lrc*, *.rtf*, *.md*, *.ini*|`none`|
 |-ver<br> -version <br> -v|Print the current version and build information. |`none`|
 |/debug|Sets up running in debug mode. If you're unsure about any response or errors you can use this flag to print all the behind the scene events. <br> This parameter does parse any argument.|`none`| 


<details>
  
  <summary> Commandline Preview [Click to reveal hidden contents.] </summary>
  
<p align="center">
  <img src="https://github.com/KabueMurage/CL-QuickTranslate/blob/master/src/img/syn.png?raw=true" alt="Commandline Syntax Preview"/>
</p>


</details>

<br>

 
 ### Demo
<p align="center">
  <img src="https://github.com/KabueMurage/CL-QuickTranslate/blob/master/src/img/demo.gif?raw=true" alt=""/>
</p>

<br>

 ### Known Issues
 
 
<details>
  
  <summary> 1. Unicode and Extended ASCII characters rendered wrongly in console window. (Displayed as question mark `?`) <br> [Expand Fix] </summary>
  
 > Although `CL-QuickTranslate` writes output based on the current console code page, which depends
 > on a system's locale by default, the current code page may handle only a subset of available Unicode
 > characters, so if you try to display characters that are not mapped to the current code page, the console 
 > won't be able to render or represent them accurately. To fix this, you can change to an active code page which may
 > allow rendering them using [chcp](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/chcp) 
 > by running the command `chcp 65001 && Cl-Quicktranslate.exe ..`. However, if you want to render Unicode output reliably ,
 > set the console font to a non-raster or TrueType font such as Consolas or Lucida Console then use 
 > logical shift or redirectional operators to parse the unicode output to file handles. Or even better, use
 > the `-o` switch which is provided as a parameter to help you to parse the output of a command to a local file that you specify.  <br>
 > Example : <br>
 > `CL-QuickTranslate.exe -s "hello world" -l ru -o "%l-HelloWorld.txt"` <br>
 > ` > Saved to file : ru-HelloWorld.txt`
 
 
</details>


<br>

### Commandline Notes

For the ```-l``` switch , all standards are backward compatible and fall back to the ISO 639-1 language prefix which is normally used by the Google Translate API ,
meaning that the command: ```Qtranslate.exe -s 'Noche Oscura' -l 'Albanian'``` (Using a native name) would be the same as running : ```Qtranslate.exe -s 'Noche Oscura' -l 'sq'``` (Using the ISO 639-1 prefix) , also the same as running:  ```Qtranslate.exe -s 'Noche Oscura' -l 'sqi'```  (Using the ISO 639-2/T prefix)  and  also the same as ```Qtranslate.exe -s 'Noche Oscura' -l 'alb'```  (Using the ISO 639-2/B prefix) <br>

The `-o` switch supports saving with specified prefixes as a substitute for special long names. : <br>

|prefix|Long name  |
|--|--|
| %l| The used ISO 639-1 language prefix. |
|%f| Used Filename without file extension. |


  Example : <br>
   `CL-QuickTranslate.exe -f "Pc Maintenance Guide.txt" -l sw -o "%l_%f.txt"` <br>
   `> Saved to file : SW_Pc Maintenance Guide.txt`  <br>

<details>
 
  <summary> Some ISO codes cheat sheet [Click to reveal hidden contents.] </summary>
  
  >  All languages standard may be used with the ```-l``` switch to set the destination language for translation.
  >  The source language is auto detected by default.
  > see full list at :https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwixuKmY9_LrAhVFCxoKHUgsB1kQFjAAegQIAxAB&url=https%3A%2F%2Fcloud.google.com%2Ftranslate%2Fdocs%2Flanguages&usg=AOvVaw0DS2aRvqlazR86JXJI1fsn
  
||ISO language name | *[ISO 639-1](https://en.wikipedia.org/wiki/ISO_639-1)*| *[ISO 639-2/T](https://en.wikipedia.org/wiki/ISO_639-2)*|*[ISO 639-2/B](https://en.wikipedia.org/wiki/ISO_639-2)*|
|--|--|--|--|--|
|1|English |*en*|*eng*|eng|
|2|Afrikaans|*af*|*afr*|afr|
|3|Albanian|*sq*|*sqi*|alb|
|4|Amharic|*am*|*amh*|amh|
|5|Arabic|*ar*|*ara*|ara|
|6|Armenian|*hy*|*hye*|arm|
|7|Azerbaijani|*az*|*aze*|-|
|8|Basque|*eu*|*eus*|baq|
|9|Belarusian|*be*|*bel*|bel|
|10|Bengali|*bn*|*ben*|ben|
|11|Bosnian|*bs*|*bos*|bos|
|12|Bulgarian|*bg*|bul|bul|
|13|Catalan,Valencian|*ca*|*cat*|cat|
|14|Cebuano|*ceb*|ceb|ceb|
|15|Chichewa|*ny*|*nya*|nya|
|16|Corsican|*co*|*cos*|cos|
|17|Croatian|*hr*|*hrv*|hrv|
|18|czech|*cs*|*ces*|cze|ces|
|19|Danish|*da*|*dan*|dan|dan|
|20|Dutch, Flemish|*nl*|*nld*|dut|
|21|Esperanto|*eo*|*epo*|epo|
|22|Estonian|*et*|est|est|
|23|Filipino|*tl*|tl|tl|
|24|Finnish|*fi*|*fin*|fin|
|25|french|*fr*|*fra*|fre|
|26|Frisian|*fy*|*fry*|fry|
|27|Georgian|*gl*|*glg*|glg|
|28|German|*de*|*deu*|ger|
|29|Haitian,Haitian Creole|*ht*|*hat*|hat|
|30|Hausa|*ha*|*hau*|hau|
|31|Hawaiian|*haw*|haw|haw|
|32|Hmong|*hmn*|hmn|hmn|
|33|Hungarian|*hu*|hun|hun|
|34|Icelandic|*is*|*isl*|ice|
|35|Igbo|*ig*|*ibo*|ibo|
|36|Indonesian|*id*|*ind*|ind|
|37|Irish|*ga*|*gle*|gle|
|38|Italian|*it*|ita|ita|
|39|Khmer|*km*|*km*|km|
|40|Latin|*la*|*lat*|lat|lat|
|41|Latvian|*lv*|*lav*|lav|
|42|Lithuanian|*lt*|*lit*|lit|
|43|Luxembourgish|*lb*|*ltz*|ltz|
|44|Malagasy|*mg*|*mlg*|mlg|
|45|Malay|*ms*|*msa*|msa|
|46|Maltese|*mt*|*mlt*|mlt|
|47|Maori|*mi*|*mri*|mao|
|48|Norwegian|*no*|*nor*|nor|
|49|Polish|*pl*|*pol*|pol|
|50|Portuguese|*pt*|*por*|por|
|51|Romanian,moldavian|*ro*|*ron*|rum|
|52|Sesotho|*st*|*sot*|sot|
|53|Slovak|*sk*|*slk*|slk|
|54|Slovenian|*sl*|*slv*|slv|
|55|Somali|*so*|*som*|som|
|56|Spanish,Castilian|*es*|*spa*|spa|
|57|Swahili, Kiswahili|*sw*|*swa*|swa|
|58|Swedish|*sv*|*swe*|swe|
|59|Turkish|*tr*|*tur*|tur|
|60|Uzbek|*uz*|*uzb*|uzb|
|61|Vietnamese|*vi*|*vie*|vie|
|62|Welsh|*cy*|*cym*|wel|
|63|Xhosa|*xh*|*xho*|xho|
|64|Yoruba|*yo*|yor|yor|
|65|Zulu|*zu*|*zul*|zul|
...

</details>

[Project Board](https://github.com/users/KabueMurage/projects/4)

###
