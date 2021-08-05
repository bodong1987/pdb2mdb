# pdb2mdb
    If you want to create a managed plugin for unity, you need provide a mdb file for debugging. With the update of VS, Unity's built-in pdb2mdb.exe may no longer work properly. Some enthusiastic netizens on the Internet provide a new pdb2mdb.exe, but I also encounter problems when using it, such as when the project is very large , Dll, pdb file size is 100M+.
    So I found the source code of pdb2mdb from the source code of mono, and tried to upgrade all its dependencies to the latest, fix the compile error by change some codes, and recompile them.
    so I got a new version of pdb2mdb, this version of pdb2mdb can solve my problem, There is no guarantee that it will solve your problem, you can try it. 
    If you want to compile this project by yourself, just open the sln file with vs2019 and compile it directly.
    prebuild release can be found in pdb2mdb/bin/Release    

    usage: makesure your dll has a pdb file, and pdb project setting is <DebugType>full</DebugType>, and then: pdb2mdb xxx.dll 
    eg : pdb2mdb D:\test.dll, don't use D:\test.pdb.
# references
    https://gist.github.com/jbevain/ba23149da8369e4a966f
    https://github.com/microsoft/cci
    https://www.nuget.org/packages/Microsoft.DiaSymReader/
    https://github.com/dotnet/symreader-converter
    https://dev.azure.com/dnceng/public/_packaging?_a=feed&feed=dotnet-tools
    https://github.com/jbevain/cecil
    https://github.com/mono/mono
    https://www.nuget.org/packages/System.Collections.Immutable/6.0.0-preview.6.21352.12
