## Assemblies
* A compiled file with an .exe of .dll file extension
* Contain metadata about all types inside
* MSCORELIB.DLL contains Console and other .NET classes
* Global Assembly Cache
  * Central location to store assemblies for a machine
  * C:\Windows\assembly
* When a project in Visual Studio is Built, an assembly is created
  * <Project folder>\bin\Debug
* Properties >> Application Tab
  * Assembly options
  * Output type: Class Library would be a .dll
* Visual Studio References holds Assemblies added to the project
* Press F12 on a class to be taken to the assmebly metadata (not quite source code)
* Use the **Object Browser** to see all the Namespaces and Types inside an assembly
* Must be loaded in memory to use an assembly
  * Easy approach - reference the assembly in Visual Studio
  * Otherwise add dependencies in project.json and other steps (Google it!)