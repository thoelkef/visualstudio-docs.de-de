---
title: "Exec Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, Exec task"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Führt das angegebene Programm oder den angegebenen Befehl mit den angegebenen Argumenten aus.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter für die `Exec`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`Command`|Erforderlicher `String`\-Parameter.<br /><br /> Die auszuführenden Befehle.  Diese können Systembefehle sein, z. B. attrib, oder eine ausführbare Datei, z. B. program.exe, runprogram.bat oder setup.msi.<br /><br /> Dieser Parameter kann mehrere Zeilen mit Befehlen enthalten.  Alternativ können Sie mehrere Befehle in eine Batchdatei einfügen und die Datei mit diesem Parameter ausführen.|  
|`CustomErrorRegularExpression`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen regulären Ausdruck an, mit dem Fehlerzeilen in der Ausgabe des Tools bestimmt werden.  Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.|  
|`CustomWarningRegularExpression`|Optionaler `String`\-Parameter.<br /><br /> Gibt einen regulären Ausdruck an, mit dem Warnungszeilen in der Ausgabe des Tools bestimmt werden.  Dies ist nützlich für Tools, die eine außergewöhnlich formatierte Ausgabe erzeugen.|  
|`ExitCode`|Optionaler schreibgeschützter `Int32`\-Ausgabeparameter.<br /><br /> Gibt den vom ausgeführten Befehl bereitgestellten Exitcode an.|  
|`IgnoreExitCode`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, ignoriert die Aufgabe den vom ausgeführten Befehl bereitgestellten Exitcode.  Andernfalls gibt die Aufgabe `false` zurück, wenn der ausgeführte Befehl einen Exitcode ungleich 0 \(null\) zurückgibt.|  
|`IgnoreStandardErrorWarningFormat`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `false`, werden Zeilen in der Ausgabe ausgewählt, die dem Standard\-Fehler\-\/Warnungsformat entsprechen, und als Fehler\/Warnungen protokolliert.  Wenn `true`, dieses Verhalten deaktivieren.|  
|`Outputs`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Ausgabeelemente der Aufgabe.  Die `Exec`\-Aufgabe legt diese nicht selbst fest.  Sie können die Ausgabeelemente so bereitstellen, als ob sie von der Aufgabe festgelegt würden, sodass sie zu einem späteren Zeitpunkt im Projekt verwendet werden können.|  
|`StdErrEncoding`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt die Codierung des aufgezeichneten Standardfehlerstreams der Aufgabe an.  Standardmäßig wird ist die aktuelle Konsolenausgabecodierung verwendet.|  
|`StdOutEncoding`|Optionaler `String`\-Ausgabeparameter.<br /><br /> Gibt die Codierung des aufgezeichneten Standardausgabestreams der Aufgabe an.  Standardmäßig wird ist die aktuelle Konsolenausgabecodierung verwendet.|  
|`WorkingDirectory`|Optionaler `String`\-Parameter.<br /><br /> Gibt das Verzeichnis an, in dem der Befehl ausgeführt wird.|  
  
## Hinweise  
 Diese Aufgabe ist nützlich, wenn eine bestimmte [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]\-Aufgabe für den Auftrag, den Sie ausführen möchten, nicht verfügbar ist.  Jedoch kann die `Exec`\-Aufgabe, im Gegensatz zu einer spezifischeren Aufgabe, nicht die Ausgabe von dem Tool oder dem Befehl sammeln, das oder der sie ausgeführt.  
  
 Die `Exec`\-Aufgabe ruft cmd.exe auf, anstatt direkt einen Prozess aufzurufen.  
  
 Zusätzlich zu den in diesem Dokument aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.ToolTaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.ToolTask>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel wird die `Exec`\-Aufgabe verwendet, um einen Befehl auszuführen.  
  
```  
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
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)