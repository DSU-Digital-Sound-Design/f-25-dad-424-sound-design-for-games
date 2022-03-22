---
title: "Fixing Unity Assembly Definition Issues"
---

Before the break we were having issues related to the Unity assembly definition.

> Assembly Definitions and Assembly References are assets that you can create to organize your scripts into assemblies.
> An assembly is a C# code library that contains the compiled classes and structs that are defined by your scripts and which also define references to other assemblies. See Assemblies in .NET for general information about assemblies in C#
>
> - [Source](https://docs.unity3d.com/Manual/ScriptCompilationAssemblyDefinitionFiles.html)

In the FPS game the designers have put each folder in the Scripts folder into a different assembly definition. Because of this separation, we need to add the Wwwise assembly definition references to each of these assembly definition scripts.

For example, open the "Game" folder in the scripts folder and find the "fps.Game" file. Find the "Assembly definition references" section and click the plus icon to add Wwise as a reference. Find the "AK.Wwise.Unity.API.WwiseTypes" reference and add it.

Repeat this process for any other assembly definition that turn up errors.
