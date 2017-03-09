---
title: "Copy Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#Copy"
  - "MSBuild.Copy.SourceFileNotFound"
  - "MSBuild.Copy.Retrying"
  - "MSBuild.Copy.ExceededRetries"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, Copy task"
  - "Copy task [MSBuild]"
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 23
caps.handback.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Copy Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Kopiert Dateien an einen neuen Speicherort im Dateisystem.  
  
## Parameter  
 In der folgenden Tabelle werden die Parameter der `Copy`\-Aufgabe beschrieben.  
  
|Parameter|Beschreibung|  
|---------------|------------------|  
|`CopiedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich kopiert wurden.|  
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die Liste der Dateien an, in die die Quelldateien kopiert werden sollen.  Diese Liste soll der im `SourceFiles`\-Parameter angegebenen Liste eins zu eins entsprechen.  Das heißt, die erste in `SourceFiles` angegebene Datei wird an den ersten in `DestinationFiles` angegebenen Speicherort kopiert usw.|  
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>\-Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien kopieren werden sollen.  Es muss sich um ein Verzeichnis handeln, nicht um eine Datei.  Wenn das Verzeichnis nicht vorhanden ist, wird es automatisch erstellt.|  
|`OverwriteReadOnlyFiles`|Optionaler `Boolean`\-Parameter.<br /><br /> Überschreibt Dateien, auch wenn diese als schreibgeschützte gekennzeichnet sind|  
|`Retries`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Anzahl der vorgesehenen Kopierversuche an, wenn alle vorherigen Versuche fehlgeschlagen sind.  Der Standardwert ist 0 \(null\).<br /><br /> **Hinweis:** Die Verwendung von Wiederholungen kann ein Synchronisierungsproblem im Buildprozess maskieren.|  
|`RetryDelayMilliseconds`|Optionaler `Int32`\-Parameter.<br /><br /> Gibt die Verzögerung zwischen jeglichen erforderlichen Wiederholungen an.  Standardwert ist das RetryDelayMillisecondsDefault\-Argument, das an den CopyTask\-Konstruktor übergeben wird.|  
|`SkipUnchangedFiles`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dateien, die an der Quelle und am Ziel identisch sind, beim Kopieren übersprungen.  In der `Copy`\-Aufgabe werden Dateien als identisch betrachtet, wenn diese dieselbe Größe aufweisen und zur selben Zeit zuletzt geändert wurden. **Note:**  Wenn Sie diesen Parameter auf `true` festlegen, sollten Sie für das enthaltende Ziel nicht die Abhängigkeitsanalyse verwenden, da die Aufgabe dann nur ausgeführt wird, wenn die letzte Änderung der Quelldateien weniger lange zurück liegt als die letzte Änderung der Zieldateien.|  
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`\-Parameter.<br /><br /> Gibt die zu kopierenden Dateien an.|  
|`UseHardlinksIfPossible`|Optionaler `Boolean`\-Parameter.<br /><br /> Wenn `true`, werden für die kopierten Dateien feste Links erstellt, statt die Dateien zu kopieren.|  
  
## Hinweise  
 Es muss entweder der `DestinationFolder`\-Parameter oder der `DestinationFiles`\-Parameter angegeben werden, jedoch nicht beide.  Wenn beide angegeben werden, schlägt die Aufgabe fehl, und ein Fehler wird protokolliert.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>\-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>\-Klasse erbt.  Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## Beispiel  
 Im folgenden Beispiel werden die Elemente in der `MySourceFiles`\-Elementauflistung in den Ordner c:\\MyProject\\Destination kopiert.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="a.cs;b.cs;c.cs"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFolder="c:\MyProject\Destination"  
        />  
    </Target>  
  
</Project>  
```  
  
## Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie ein rekursiver Kopiervorgang ausgeführt wird.  In diesem Projekt werden alle Dateien rekursiv von c:\\MySourceTree nach c:\\MyDestinationTree kopiert, wobei die Verzeichnisstruktur beibehalten wird.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <MySourceFiles Include="c:\MySourceTree\**\*.*"/>  
    </ItemGroup>  
  
    <Target Name="CopyFiles">  
        <Copy  
            SourceFiles="@(MySourceFiles)"  
            DestinationFiles="@(MySourceFiles->'c:\MyDestinationTree\%(RecursiveDir)%(Filename)%(Extension)')"  
        />  
    </Target>  
  
</Project>  
```  
  
## Siehe auch  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)