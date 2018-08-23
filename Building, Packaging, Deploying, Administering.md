---
title: Building, Packaging, Deploying, Administering 
tags: C#
grammar_cjkRuby: true
grammar_tableExtra: true
---
# Building, Packaging, Deploying, Administering
## Building Types into a Module
* csc usage: csc.exe /out:Program.exe /t:exe /r:MSCorLib.dll Program.cs
	* MSCorLib.cll: core types, System Libs, could be omitted in command line.
		* to disable this linkage: /nostdlib
	* /t : target, CUI = exe, GUI = winexe, WinStoreApp = appcontainerexe
	* library fallbacks:
		* working directory.
		* csc.exe file containing folder
		* /lib: compiler search folder
		* LIB environment variable folder
* Response File: makefile like file for csc
	* csc.exe @file.rsp code1.cs code2.cs
	* /noconfig: drop local and global rsp files
```makefile
/out:MyProject.exe
/target:winexe
```
## Metadata
* Managed PE file
	* PE32+ header: Windows std info
	* CLR header: required CLR modules
		* Check CorHdr.h -> IMAGE_COR20_HEADER
	* Metadata
		* Definition Table
		* Reference Table
		* Manifest Table
	* IL

Metadata Definition Table Name|Description
----|----
ModuleDef|one entry identify the module.<br>Module filename + extension + versionID
TypeDef|one entry for each type in the module.<br>Type name+base type+flags+n_MethodDef+<br>n_FieldDef + n_PropertyDef + n_EventDef
MethodDef|one entry for each method.<br>name + flags + signature + offset of IL code + n_Paramdef
FieldDef|one entry for every field.<br>flags + type + name
ParamDef|one entry for each parameter.<br>flags + type + name
PropertyDef|one entry for each property.<br>flags + type + name
EventDef|one entry for each event.<br>flags + name|
[Common Definition Metadata Table]

|Metadata Reference Table Name |Description|
|----|----|
AssemblyRef | one entry for each assembly referenced by module.<br>name + version + culture + public key token + <br> flags + checksum
ModuleRef | one entry for each PE module that implements types referenced by the module.<br> filename + extension
TypeRef | one entry for each type referenced by the module. <br> type name + reference (TypeRef | ModuleDef|ModuleRef|AssemblyRef)
MemberRef|one entry foreach member referenced by the module.<br>member name + signature + TypeRef for the type.
[Common Reference Metadata Table]

## Combining Modules to Form an Assembly
* Assembly
	* manifest: names of files, version, culture, publisher, exported types
	* reusable types
	* version number
	* security infos
* Assembly decouple logical & physical notion of reusable types

Manifest Metadata Table Name | Description
|----|----|
Assembly Def|assembly name + version + culture + flags + hash + public key
FileDef|one for each PE and resource file.<br> filename + extension + hash value + flags
ManifestResourceDef|one for each resource.<br>name + flags + n_FileDef
ExportedTypesDef|One Entry for each public type from all the PE modules.<br>name + n_FileDef, n_TypeDef_internal
[Manifest Metadata Table]

* Compile into assembly
	* /t:exe, CUI
	* /t:winexe , GUI
	* /t:appcontainerexe , Windows Store executable
	* /t:library , class library
	* /t:winmdobj , WINMD library, object must be passed to WinMDExp.exe tool 
	* /t:module: produce a PE without manifest, part of DLL, manifested by other assembly. /out:a.netmodule
		* add a module: /addmodule
		* when build, all files reference should be present
		* when runtime, lazy loading

## Use assembly linker, al

## Adding Resource Files to an Assembly
* AL:
	* /embed: embed resources
	* /link: file itself not embedded
* csc
	* /resource
	* /linkresource
* to embed win32 resource
	* .res file, /win32res
	* .ico file, /win32icon
* AL check version resource files
	* /fileversion
	* /poductversion
	* FILEFLAGSMASK
	* FILEFLAGS = 0
	* FILEOS = VOS__WINDOWS32
	* /target
	* FILESUBTYPE = VFT_UNKNOWN
	* /version
	* /description
	* /company
	* /title
	* /version
	* /out
	* /copyright
	* /trademark
	* PRIVATEBUILD =
	* /product
	* /productversion
	* SPECIALBUILD = 
## Simple App Deploy, Privately depolyed assemblies

* WinStore - appx.
* Desktop - just files
* MSIExec.exe
* VS publish

## Simple Administrative Control
* Program.exe.config
```xml
<configuration>
    <runtime>
	    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
		    <probing privatePath="AuxFiles" />
		</assemblyBinding>
	</runtime>
</configuration>
```

