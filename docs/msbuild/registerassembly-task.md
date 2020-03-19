---
title: RegisterAssembly-Aufgabe | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c95606a00e86ffd187162e444f2c710c5cc3a0e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632887"
---
# <a name="registerassembly-task"></a>RegisterAssembly-Aufgabe

Liest die Metadaten in der angegebenen Assembly und fügt die erforderlichen Einträge zur Registrierung hinzu. COM-Clients sind so in der Lage, .NET Framework-Klassen transparent zu erstellen. Das Verhalten dieser Aufgabe ähnelt dem von [Regasm.exe (Assemblyregistrierungstool)](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), ist aber nicht identisch.

## <a name="parameters"></a>Parameter

 In der folgenden Tabelle werden die Parameter der `RegisterAssembly`-Aufgabe beschrieben.

|Parameter|Beschreibung|
|---------------|-----------------|
|`Assemblies`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die mit COM zu registrierenden Assemblys an.|
|`AssemblyListFile`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>-Parameter.<br /><br /> Enthält Informationen zum Zustand zwischen der `RegisterAssembly`-Aufgabe und der [UnregisterAssembly](../msbuild/unregisterassembly-task.md)-Aufgabe. Diese Informationen verhindern, dass die `UnregisterAssembly`-Aufgabe versucht, die Registrierung einer Assembly aufzuheben, die in der `RegisterAssembly`-Aufgabe nicht registriert werden konnte.|
|`CreateCodeBase`|Optionaler `Boolean`-Parameter.<br /><br /> Wenn `true`, wird ein Codebase-Eintrag in der Registrierung erstellt, der den Dateipfad für eine Assembly festlegt, die nicht im globalen Assemblycache installiert ist. Die Option sollte nicht angegeben werden, wenn Sie die zu registrierende Assembly später im globalen Assemblycache installieren.|
|`TypeLibFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Gibt die Typbibliothek an, die aus der angegebenen Assembly generiert werden soll. Die generierte Typbibliothek enthält Definitionen der in der Assembly definierten Typen, auf die zugegriffen werden kann. Die Typbibliothek wird nur generiert, wenn eine der folgenden Bedingungen zutrifft:<br /><br /> – Eine Typbibliothek mit diesem Namen ist an diesem Speicherort nicht vorhanden.<br />- Eine Typbibliothek ist vorhanden, jedoch älter als die übergebene Assembly.<br /><br /> Wenn die Typbibliothek neuer ist als die übergebene Assembly, wird keine neue erstellt, aber die Assembly wird immer noch registriert.<br /><br /> Wenn dieser Parameter angegeben wird, muss er die gleiche Anzahl von Elementen wie der `Assemblies`-Parameter haben, oder bei der Aufgabe tritt ein Fehler auf. Wenn keine Eingaben angegeben werden, erhält die Aufgabe standardmäßig den Namen der Assembly und ändert die Erweiterung des Elements in *TLB*.|

## <a name="remarks"></a>Bemerkungen

 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension-Basisklasse](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Beispiel

 Im folgenden Beispiel wird die von der Elementsammlung `RegisterAssembly` angegebene Assembly mithilfe der `MyAssemblies`-Aufgabe registriert.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyAssemblies Include="MyAssembly.dll" />
    <ItemGroup>

    <Target Name="RegisterAssemblies">
        <RegisterAssembly
            Assemblies="@(MyAssemblies)" >
    </Target>

</Project>
```

## <a name="see-also"></a>Weitere Informationen

- [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)
- [Referenz zu MSBuild-Tasks](../msbuild/msbuild-task-reference.md)
