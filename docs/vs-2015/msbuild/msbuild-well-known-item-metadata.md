---
title: Bekannte MSBuild-Elementmetadaten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, item metadata
- MSBuild, well-known item metadata
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d8d83c6eaf441b72bc3774f4117653826da47613
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49234051"
---
# <a name="msbuild-well-known-item-metadata"></a>MSBuild bekannte Elementmetadaten
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
In der folgenden Tabelle werden die jedem Element bei der Erstellung zugewiesenen Metadaten beschrieben. In jedem Beispiel wurde die folgende Elementdeklaration verwendet, um die Datei `C:\MyProject\Source\Program.cs` in das Projekt aufzunehmen.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Elementmetadaten|Beschreibung|  
|-------------------|-----------------|  
|%(FullPath)|Enthält den vollständigen Pfad des Elements. Zum Beispiel:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Enthält das Stammverzeichnis des Elements. Zum Beispiel:<br /><br /> `C:\`|  
|%(Filename)|Enthält den Dateinamen des Elements ohne Erweiterung. Zum Beispiel:<br /><br /> `Program`|  
|%(Erweiterung)|Enthält die Dateinamenerweiterung des Elements. Zum Beispiel:<br /><br /> `.cs`|  
|%(RelativeDir)|Enthält den im `Include`-Attribut angegebenen Pfad, bis zum abschließenden umgekehrten Schrägstrich (\\). Zum Beispiel:<br /><br /> `Source\`|  
|%(Directory)|Enthält das Verzeichnis des Elements ohne das Stammverzeichnis. Zum Beispiel:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Wenn das `Include`-Attribut das Platzhalterzeichen \*\* enthält, geben diese Metadaten den Teil des Pfads an, der das Platzhalterzeichen ersetzt. Weitere Informationen zu Platzhaltern finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Wenn der Ordner *C:\MySolution\MyProject\Source\\* die Datei „Program.cs“ enthält, und wenn die Projektdatei dieses Element enthält:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> ist der Wert von `%(MyItem.RecursiveDir)` gleich *\MyProject\Source\\*.|  
|%(Identity)|Das im `Include`-Attribut angegebene Element. Zum Beispiel:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Enthält den Zeitstempel vom Zeitpunkt der letzten Änderung des Elements. Zum Beispiel:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Enthält den Zeitstempel vom Zeitpunkt der Erstellung des Elements. Zum Beispiel:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Enthält den Zeitstempel vom Zeitpunkt des letzten Zugriffs auf das Element.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Siehe auch  
 [Elemente](../msbuild/msbuild-items.md)   
 [Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)



