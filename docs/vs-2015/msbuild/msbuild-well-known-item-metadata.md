---
title: Bekannte MSBuild-Elementmetadaten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: abf45460ec924aea7a6c1c18244aa7661c52d42f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790186"
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
|%(FullPath)|Enthält den vollständigen Pfad des Elements. Beispiel:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%(RootDir)|Enthält das Stammverzeichnis des Elements. Beispiel:<br /><br /> `C:\`|  
|%(Filename)|Enthält den Dateinamen des Elements ohne Erweiterung. Beispiel:<br /><br /> `Program`|  
|%(Erweiterung)|Enthält die Dateinamenerweiterung des Elements. Beispiel:<br /><br /> `.cs`|  
|%(RelativeDir)|Enthält den im `Include`-Attribut angegebenen Pfad, bis zum abschließenden umgekehrten Schrägstrich (\\). Beispiel:<br /><br /> `Source\`|  
|%(Directory)|Enthält das Verzeichnis des Elements ohne das Stammverzeichnis. Beispiel:<br /><br /> `MyProject\Source\`|  
|%(RecursiveDir)|Wenn das `Include`-Attribut das Platzhalterzeichen \*\* enthält, geben diese Metadaten den Teil des Pfads an, der das Platzhalterzeichen ersetzt. Weitere Informationen zu Platzhaltern finden Sie unter [Vorgehensweise: Auswählen von Dateien für den Buildvorgang](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Wenn der Ordner *C:\MySolution\MyProject\Source\\* die Datei „Program.cs“ enthält, und wenn die Projektdatei dieses Element enthält:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> ist der Wert von `%(MyItem.RecursiveDir)` gleich *\MyProject\Source\\*.|  
|%(Identity)|Das im `Include`-Attribut angegebene Element. Beispiel:<br /><br /> `Source\Program.cs`|  
|%(ModifiedTime)|Enthält den Zeitstempel vom Zeitpunkt der letzten Änderung des Elements. Beispiel:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%(CreatedTime)|Enthält den Zeitstempel vom Zeitpunkt der Erstellung des Elements. Beispiel:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%(AccessedTime)|Enthält den Zeitstempel vom Zeitpunkt des letzten Zugriffs auf das Element.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## <a name="see-also"></a>Siehe auch  
 [Elemente](../msbuild/msbuild-items.md)   
 [Batching (Batchverarbeitung)](../msbuild/msbuild-batching.md)   
 [MSBuild-Referenz](../msbuild/msbuild-reference.md)
