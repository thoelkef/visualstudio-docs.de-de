---
title: 'Vorgehensweise: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, building specific targets in a solution
- msbuild.exe, building specific targets in a solution
- MSBuild, msbuild.exe
ms.assetid: f46feb9b-4c16-4fec-b6e1-36a959692ba3
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 4437c8030f66ae24d94a83d796c0d0edf7e59c79
ms.sourcegitcommit: 8cbe6b38b810529a6c364d0f1918e5c71dee2c68
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-build-specific-targets-in-solutions-by-using-msbuildexe"></a>Gewusst wie: Erstellen von bestimmten Zielen in Projektmappen mit MSBuild.exe
Sie können MSBuild.exe verwenden, um bestimmte Ziele von bestimmten Projekten in einer Projektmappe zu erstellen.  
  
### <a name="to-build-a-specific-target-of-a-specific-project-in-a-solution"></a>So erstellen Sie ein bestimmtes Ziel von einem bestimmten Projekt in einer Projektmappe.  
  
1.  Geben Sie in der Befehlszeile `MSBuild.exe <SolutionName>.sln` ein, bei der `<SolutionName>` dem Dateinamen der Projektmappe entspricht, die das Ziel enthält, das Sie ausführen möchten.  
  
2. Geben Sie das Ziel nach dem `/target:`-Schalter im Format **`ProjectName`**`:`**`TargetName`** an. Wenn eines der Zeichen `%`, `$`, `@`, `;`, `.`, `(`, `)` oder `'` im Namen des Projekts enthalten ist, ersetzen Sie es im angegebenen Zielnamen durch `_`.
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel führt das Ziel `Rebuild` des Projekts `NotInSlnFolder` aus und führt anschließend das Ziel `Clean` des Projekts `InSolutionFolder` aus, das im Projektmappenordner `NewFolder` ist .  
  
```
msbuild SlnFolders.sln /target:NotInSlnfolder:Rebuild;NewFolder\InSolutionFolder:Clean`
```

## <a name="troubleshooting"></a>Problembehandlung

Wenn Sie die für Sie verfügbaren Optionen überprüfen möchten, können Sie hierfür eine von MSBuild bereitgestellte Debugoption verwenden. Legen Sie die Umgebungsvariable `MSBUILDEMITSOLUTION=1` fest, und erstellen Sie Ihre Projektmappe. Dadurch wird eine MSBuild-Datei namens `<SolutionName>.sln.metaproj` erzeugt, die die interne MSBuild-Ansicht der Projektmappe zur Buildzeit anzeigt. Anhand dieser Ansicht können Sie feststellen, welche Ziele für das Build verfügbar sind.

Erstellen Sie mit dieser Umgebungsvariable nur dann Ziele, wenn Sie diese interne Ansicht benötigen. Diese Einstellung kann zu Problemen beim Erstellen von Projekten in Ihrer Projektmappe führen.

## <a name="see-also"></a>Siehe auch  
 [Befehlszeilenreferenz](../msbuild/msbuild-command-line-reference.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)   
 [MSBuild](../msbuild/msbuild.md)  
 [MSBuild-Grundlagen](../msbuild/msbuild-concepts.md)
