---
title: Exec-Aufgabe | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a9c1338910364451577957da52f9f3aef518aa67
ms.openlocfilehash: e8c9e615d8bf88a897add6b139d27c617fbec018
ms.lasthandoff: 02/22/2017

---
# <a name="exec-task"></a>Exec-Aufgabe
Führt das angegebene Programm oder den Befehl mit den angegebenen Argumenten aus.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter für die `Exec`-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|-----------------|  
|`Command`|Erforderlicher `String`-Parameter.<br /><br /> Der/die auszuführende(n) Befehl(e). Dies kann ein Systembefehl sein, z.B. „attrib“, oder eine ausführbare Datei wie „program.exe“, „runprogram.bat“ oder „setup.msi“.<br /><br /> Dieser Parameter kann mehrere Zeilen mit Befehlen enthalten. Alternativ können Sie mehrere Befehle in einer Batchdatei speichern und sie ausführen, indem Sie diesen Parameter verwenden.|  
|`CustomErrorRegularExpression`|Optionaler `String` -Parameter.<br /><br /> Legt einen regulären Ausdruck fest, der verwendet wird, um Fehlerzeilen in der Ausgabe des Tools zu erkennen. Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.|  
|`CustomWarningRegularExpression`|Optionaler `String` -Parameter.<br /><br /> Legt einen regulären Ausdruck fest, der verwendet wird, um Warnungszeilen in der Ausgabe des Tools zu erkennen. Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.|  
|`ExitCode`|Optionaler schreibgeschützter `Int32`-Ausgabeparameter.<br /><br /> Gibt den durch den ausgeführten Befehl bereitgestellten Exitcode an.|  
|`IgnoreExitCode`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, ignoriert die Aufgabe den durch den ausgeführten Befehl bereitgestellten Exitcode. Andernfalls gibt die Aufgabe `false` zurück, wenn der ausgeführte Befehl einen Exitcode ungleich null (0) zurückgibt.|  
|`IgnoreStandardErrorWarningFormat`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `false`, werden Zeilen in der Ausgabe ausgewählt, die dem standardmäßigen Fehler-/Warnungsformat entsprechen, und als Fehler/Warnungen protokolliert. Wenn `true`, wird dieses Verhalten deaktiviert. Der Standardwert ist `false`.|  
|`Outputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Ausgabeparameter.<br /><br /> Enthält die Ausgabeelemente aus der Aufgabe. Die `Exec`-Aufgabe legt diese nicht selbst fest. Stattdessen können Sie sie so bereitstellen, als ob die Aufgabe sie festgelegt hätte, damit sie später im Projekt verwendet werden können.|  
|`StdErrEncoding`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Codierung des standardmäßigen Fehlerdatenstroms der erfassten Aufgabe an. Der Standardwert ist die aktuelle Konsolenausgabencodierung.|  
|`StdOutEncoding`|Optionaler `String`-Ausgabeparameter.<br /><br /> Gibt die Codierung des standardmäßigen Ausgabedatenstroms der erfassten Aufgabe an. Der Standardwert ist die aktuelle Konsolenausgabencodierung.|  
|`WorkingDirectory`|Optionaler `String` -Parameter.<br /><br /> Gibt das Verzeichnis an, in dem der Befehl ausgeführt wird.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Aufgabe ist nützlich, wenn eine bestimmte [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]-Aufgabe für den Auftrag, den Sie ausführen möchten, nicht verfügbar ist. Allerdings kann die `Exec`-Aufgabe im Gegensatz zu einer spezifischeren Aufgabe weder Ausgaben des Tools erfassen noch Befehle, die es ausführt.  
  
 Die `Exec`-Aufgabe ruft „cmd.exe“ auf, anstatt direkt einen Prozess aufzurufen.  
  
 Neben den in diesem Dokument genannten Parametern übernimmt diese Aufgabe Parameter von der Klasse <xref:Microsoft.Build.Tasks.ToolTaskExtension>, die diese wiederum von der Klasse <xref:Microsoft.Build.Utilities.ToolTask> übernimmt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension-Basisklasse](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird die `Exec`-Aufgabe zum Ausführen eines Befehls verwendet.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md) (MSBuild-Aufgabenreferenz)

