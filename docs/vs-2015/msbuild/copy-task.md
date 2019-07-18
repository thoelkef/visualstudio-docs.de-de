---
title: Copy-Aufgabe | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Copy
- MSBuild.Copy.SourceFileNotFound
- MSBuild.Copy.Retrying
- MSBuild.Copy.ExceededRetries
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Copy task
- Copy task [MSBuild]
ms.assetid: a46ba9da-3e4e-4890-b4ea-09a099b6bc40
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 08442d6044ca978e69f199e76c4668db63c319da
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196587"
---
# <a name="copy-task"></a>Copy-Aufgabe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kopiert Dateien an einen neuen Speicherort im Dateisystem.  
  
## <a name="parameters"></a>Parameter  
 In der folgenden Tabelle werden die Parameter der `Copy` -Aufgabe beschrieben.  
  
|Parameter|BESCHREIBUNG|  
|---------------|-----------------|  
|`CopiedFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]` -Ausgabeparameter.<br /><br /> Enthält die Elemente, die erfolgreich kopiert wurden.|  
|`DestinationFiles`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter<br /><br /> Gibt die Liste der Dateien an, in die die Quelldateien kopiert werden sollen. Diese Liste soll der im `SourceFiles`-Parameter angegebenen Liste eins zu eins entsprechen. Das heißt, die erste in `SourceFiles` angegebene Datei wird an den ersten in `DestinationFiles` angegebenen Speicherort kopiert usw.|  
|`DestinationFolder`|Optionaler <xref:Microsoft.Build.Framework.ITaskItem> -Parameter.<br /><br /> Gibt das Verzeichnis an, in das die Dateien kopieren werden sollen. Es muss sich um ein Verzeichnis handeln, nicht um eine Datei. Wenn das Verzeichnis nicht vorhanden ist, wird es automatisch erstellt.|  
|`OverwriteReadOnlyFiles`|Optionaler `Boolean` -Parameter.<br /><br /> Überschreibt Dateien, auch wenn diese als schreibgeschützte gekennzeichnet sind|  
|`Retries`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die Anzahl der vorgesehenen Kopierversuche an, wenn alle vorherigen Versuche fehlgeschlagen sind. Der Standardwert ist 0 (null).<br /><br /> **Hinweis:** Die Verwendung von Wiederholungen kann ein Synchronisierungsproblem im Buildprozess maskieren.|  
|`RetryDelayMilliseconds`|Optionaler `Int32` -Parameter.<br /><br /> Gibt die Verzögerung zwischen jeglichen erforderlichen Wiederholungen an. Standardwert ist das RetryDelayMillisecondsDefault-Argument, das an den CopyTask-Konstruktor übergeben wird.|  
|`SkipUnchangedFiles`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn der Wert `true` lautet, werden Dateien, die an der Quelle und am Ziel identisch sind, beim Kopieren übersprungen. In der `Copy`-Aufgabe werden Dateien als identisch betrachtet, wenn diese dieselbe Größe aufweisen und zur selben Zeit zuletzt geändert wurden. **Hinweis:** Wenn Sie diesen Parameter auf `true` festlegen, sollten Sie für das enthaltende Ziel aus folgendem Grund nicht die Abhängigkeitsanalyse verwenden: Die Aufgabe wird nur dann ausgeführt, wenn die letzte Änderung der Quelldateien weniger lange zurück liegt als die letzte Änderung der Zieldateien.|  
|`SourceFiles`|Erforderlicher <xref:Microsoft.Build.Framework.ITaskItem>`[]`-Parameter.<br /><br /> Gibt die zu kopierenden Dateien an.|  
|`UseHardlinksIfPossible`|Optionaler `Boolean` -Parameter.<br /><br /> Wenn `true`, werden für die kopierten Dateien feste Links erstellt, statt die Dateien zu kopieren.|  
  
## <a name="warnings"></a>Warnungen  
 Warnungen werden protokolliert, darunter:  
  
- `Copy.DestinationIsDirectory`  
  
- `Copy.SourceIsDirectory`  
  
- `Copy.SourceFileNotFound`  
  
- `Copy.CreatesDirectory`  
  
- `Copy.HardLinkComment`  
  
- `Copy.RetryingAsFileCopy`  
  
- `Copy.FileComment`  
  
- `Copy.RemovingReadOnlyAttribute`  
  
## <a name="remarks"></a>Anmerkungen  
 Es muss entweder der `DestinationFolder`-Parameter oder der `DestinationFiles`-Parameter angegeben werden, jedoch nicht beide. Wenn beide angegeben werden, schlägt der Task fehl, und ein Fehler wird protokolliert.  
  
 Zusätzlich zu den oben aufgeführten Parametern erbt diese Aufgabe Parameter von der <xref:Microsoft.Build.Tasks.TaskExtension>-Klasse, die selbst von der <xref:Microsoft.Build.Utilities.Task>-Klasse erbt. Eine Liste mit diesen zusätzlichen Parametern und ihren Beschreibungen finden Sie unter [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Elemente in der `MySourceFiles`-Elementauflistung in den Ordner c:\MyProject\Destination kopiert.  
  
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
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird veranschaulicht, wie ein rekursiver Kopiervorgang ausgeführt wird. In diesem Projekt werden alle Dateien rekursiv von c:\MySourceTree nach c:\MyDestinationTree kopiert, wobei die Verzeichnisstruktur beibehalten wird.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Tasks (Aufgaben)](../msbuild/msbuild-tasks.md)   
 [Aufgabenreferenz](../msbuild/msbuild-task-reference.md)
