# Pas2js Pascal to JavaScript transpiler for Delphi
Here you will find Pas2JS - Pascal to JavaScript transpiler adaptation for Delphi compiler. It takes Delphi/Lazarus projects and modules (.DPR, .LPR, .PAS) and converts them to JavaScript (.JS). The original transpiler for Free Pascal is [here](http://wiki.freepascal.org/pas2js).

This adaptation based on Pas2JS for FPC dated **January 30, 2022**, downloaded from [GitLab](https://gitlab.com/freepascal.org/fpc/pas2js).

## Most important changes
There are no any modifications in my edition other than those needed to compile it in Delphi for Windows:
* Used Unicode UTF-16 instead of UTF-8 (and ANSI) strings in the transpiler code.
* Used generic collections (TDictionary<string, XXX>) instead of TFPHashObjectList.

## Other changes caused by syntax differences between Free Pascal and Delphi:
* case statement for strings --> if string = ... then else if string = ... then ...
* for item in enumeration do --> for item := Low(TEnumeration) to High(TEnumeration) do ...

## Limitation of Pas2js edition for Delphi
The original Pas2js supports several operation systems and compilation targets. This Pas2js for Delphi
* has the pas2js.dpr command-line utility for **Windows** only, **32-bit** and **64-bit** platforms.
* The utility was tested for the **browser** and **nodejs** target platforms, i.e. it can generate JS files to use in HTML pages and NodeJS.
* However it can compile the Web Pas2JS compiler, which can be used online on your server. See WebCompiler demo program.
* The original Pas2JS source files not used in this Delphi adaptation have been removed from the package.

## Testing and compatibility
Pas2js for Delphi was developed using Delphi 10.4.2 and tested against the demos included in the original package. This includes: basic RTL tests, Charts, Bootstrap, Pacman and Tetris web games, WebGL, etc.

It is guaranteed that the output JS, MAP and HTML files generated by the original Pas2js for FPC and this adaptation are exactly the same. The only exception is floating point representation:
|Source Pascal constant|Pas2JS for FPC|Pas2JS for Delphi (this adaptation)|
|---|---|---|
|`hrfactor = 1/(24);`|`0.041666666666666664`|`0.0416666666666667`|
|`mssecfactor = 1/(24*60*60*1000);|`1.1574074074074074E-8`|`1.15740740740741E-8`|

You can use any edition of Delphi to compile the project, including [the free Community edition](https://www.embarcadero.com/products/delphi/starter).

## Support and updates
I cannot guarantee that Pas2js for Delphi will be updated regularly to keep pace with Pas2js for FPC. The reason I made this adaptation is because Delphi is my main development IDE. I prefer to work with all my projects in one convenient environment.

## License
Pas2js has the same license as the original Pas2js for FPC. It is essentially GNU General Public License with one modification.

(C) 2022 Kryvich.
