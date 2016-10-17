# PowershellTools

## dll2ps (Support DllRegisterServer)
    powershell.exe -ep bypass -f dll2ps.ps1 -File test.dll -Out out.ps1
  
## exe2ps
    powershell.exe -ep bypass -f exe2ps.ps1 -File test.exe -Param "hello world" -Out out.ps1
