# IDA_PHNT_TYPES
Converted phnt (Native API header files from the System Informer project) to IDA TIL, IDC (Hex-Rays).<br/>
To import "phnt" types and function definitions to IDA and help with Reverse Engineering.<br/>

## Using
- Windows 11 SDK 10.0.22621.0<br/>
- Latest phnt (08-23-2024)<br/>
- PHNT_VERSION PHNT_WIN11 // Windows 11 - To get latest types<br/>
- IDA Tools: idaclang84, tilib84<br/>
<br/>

## Generated Converted Output
### IDA IDC "phnt" Type Information Scripts
- **Files:** phnt_win11.idc, phnt64_win11.idc<br/>
- **Contains:** phnt types, no function definitions<br/>
- **Usage:** In IDA, execute the *.idc script file and types should be imported - check the "Local Types" window.<br/>

### IDA TIL "phnt" Type Information Libraries
- **Files:** phnt_win11.til, phnt64_win11.til<br/>
- **Contains:** phnt types + function definitions<br/>
- **Usage:** <br/>
Copy *.til files to your "IDA Instalation Dir\til\pc", e.g., "C:\Program Files\IDA Pro 8.4\til\pc".<br/>
In IDA, go to "Type Libraries" window and load the appropriate *.til type library.<br/>
<br/>

## Compilation Commands
Make sure that the appropriate version of Windows SDK (Windows 11 SDK) is installed (use Visual Studio installer).<br/>
Copy idaclang.exe to your "IDA Instalation Dir", e.g., "C:\Program Files\IDA Pro 8.4".<br/>

### To generate IDA TIL "phnt" Type Information Libraries:
**phnt_win11.til:** <br/>
`.\idaclang.exe -target i386-pc-win32 -x c++ -I"C:\Users\User\Desktop\IDA_PHNT_TYPES\phnt" --idaclang-tildesc "PHNT Native API Header Files (Windows 11)" --idaclang-tilname "phnt_win11.til" phnt_include.h`<br/>

**phnt64_win11.til:** <br/>
`.\idaclang.exe -target x86_64-pc-win32 -x c++ -I"C:\Users\User\Desktop\IDA_PHNT_TYPES\phnt" --idaclang-tildesc "PHNT Native API Header Files (Windows 11 x64)" --idaclang-tilname "phnt64_win11.til" phnt_include.h`<br/>

**Check types in TIL:** <br/>
Copy tilib64.exe to your "IDA Instalation Dir", e.g., "C:\Program Files\IDA Pro 8.4".<br/>
`.\tilib64.exe -l .\phnt_win11.til`<br/>
`.\tilib64.exe -l .\phnt64_win11.til`<br/>
<br/>

### To generate IDA IDC "phnt" Type Information Scripts:
Very similar like above but using the IDA UI, setting the Options->Compiler (Source parser=clang, target, included directories).<br/>
`IDA-> Load File-> Parse C header file` (phnt_include.h)<br/>
`IDA-> Produce file -> Dump typeinfo to IDC file`<br/>
<br/>

## BEFORE vs. AFTER
![](pics/ntdll_before_vs_after.png)
<br/>

## License
**NO** :grin:<br/>
<br/>
![](pics/license.jpg)<br/><br/>

## Reference
- [phnt - Native API header files for the System Informer project](https://github.com/winsiderss/phnt)<br/>
- [IDA](https://hex-rays.com/)<br/>
- [IDA idaclang tutorial](https://hex-rays.com/tutorials/idaclang/idaclang_tutorial.pdf)<br/>
- [IDA idaclang example](https://blog.nviso.eu/2023/11/07/generating-ida-type-information-libraries-from-windows-type-libraries/)<br/>
