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

