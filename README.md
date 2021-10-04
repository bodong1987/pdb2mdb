# pdb2mdb
        If you want to create a managed plugin for unity3d engine, you need provide a mdb file for debugging. With the update of VS, Unity's built-in pdb2mdb.exe may no longer work properly. Some enthusiastic netizens on the Internet provide a new pdb2mdb.exe, but I also encounter problems when using it, such as when the project is very large , Dll, pdb file size is 100M+.
    the common error like this:
            Fatal error:
                Microsoft.Cci.Pdb.PdbDebugException: Invalid signature. (sig=1919117645)
                in Microsoft.Cci.Pdb.PdbFile.LoadFuncsFromDbiModule(BitAccess bits, DbiModuleInfo info, IntHashTable names, ArrayList funcList, Boolean readStrings, MsfDirectory dir, Dictionary`2 nameIndex, PdbReader reader)
                in Microsoft.Cci.Pdb.PdbFile.LoadFunctions(Stream read, BitAccess bits, Boolean readAllStrings)
                in Pdb2Mdb.Driver.Convert(AssemblyDefinition assembly, Stream pdb, MonoSymbolWriter mdb)

        So I found the source code of pdb2mdb from the source code of mono, and tried to upgrade all its dependencies to the latest, fix the compile error by change some codes which is not compatible with the new codes, and recompile them.
        so I got a new version of pdb2mdb, this version of pdb2mdb can solve my problem, There is no guarantee that it will solve your problem, you can try it. 
        If you want to compile this project by yourself, just open the sln file with vs2019 and compile it directly.
    prebuild release can be found in pdb2mdb/bin/Release    

    usage: makesure your dll has a pdb file, and project settings <DebugType>full</DebugType>, and then: pdb2mdb xxx.dll 
    eg : pdb2mdb.exe D:\test.dll
    don't use D:\test.pdb
    
# references

pdb2mdb.exe<br><https://gist.github.com/jbevain/ba23149da8369e4a966f><br>
microsoft.cci<br><https://github.com/microsoft/cci><br>
DiaSymReader<br><https://www.nuget.org/packages/Microsoft.DiaSymReader/><br>
DiaSymReader.Converter<br><https://github.com/dotnet/symreader-converter><br>
DiaSymReader.Converter Prebuild Binaries<br><https://dev.azure.com/dnceng/public/_packaging?_a=feed&feed=dotnet-tools><br>
Mono.Cecil<br><https://github.com/jbevain/cecil><br>
Mono<br><https://github.com/mono/mono><br>
System.Collections.Immutable<br><https://www.nuget.org/packages/System.Collections.Immutable/6.0.0-preview.6.21352.12><br>
