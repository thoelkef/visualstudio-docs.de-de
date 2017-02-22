---
title: "MSBuild Well-known Item Metadata | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, item metadata"
  - "MSBuild, well-known item metadata"
ms.assetid: b5e791b5-c68f-4978-ad8a-9247d03bb6c0
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MSBuild Well-known Item Metadata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In der folgenden Tabelle werden die jedem Element bei der Erstellung zugewiesenen Metadaten beschrieben.  In jedem Beispiel wurde die folgende Elementdeklaration verwendet, um die Datei `C:\MyProject\Source\Program.cs` in das Projekt aufzunehmen.  
  
```  
<ItemGroup>  
    <MyItem Include="Source\Program.cs" />  
</ItemGroup>  
```  
  
|Elementmetadaten|Beschreibung|  
|----------------------|------------------|  
|%\(FullPath\)|Enthält den vollständigen Pfad des Elements.  Beispiel:<br /><br /> `C:\MyProject\Source\Program.cs`|  
|%\(RootDir\)|Enthält das Stammverzeichnis des Elements.  Beispiel:<br /><br /> `C:\`|  
|%\(Filename\)|Enthält den Dateinamen des Elements ohne Erweiterung.  Beispiel:<br /><br /> `Program`|  
|%\(Extension\)|Enthält die Dateinamenerweiterung des Elements.  Beispiel:<br /><br /> `.cs`|  
|%\(RelativeDir\)|Enthält den im `Include`\-Attribut angegebenen Pfad, bis zum abschließenden umgekehrten Schrägstrich \(\\\).  Beispiel:<br /><br /> `Source\`|  
|%\(Directory\)|Enthält das Verzeichnis des Elements ohne das Stammverzeichnis.  Beispiel:<br /><br /> `MyProject\Source\`|  
|%\(RecursiveDir\)|Wenn das `Include`\-Attribut das Platzhalterzeichen "\*\*" enthält, geben diese Metadaten den Teil des Pfads an, der das Platzhalterzeichen ersetzt.  Weitere Informationen zu Platzhaltern finden Sie unter [How to: Select the Files to Build](../msbuild/how-to-select-the-files-to-build.md).<br /><br /> Wenn der Ordner *C:\\MySolution\\MyProject\\Source\\* die Datei "Program.cs" enthält und die Projektdatei dieses Element enthält:<br /><br /> `<ItemGroup>`<br /><br /> `<MyItem Include="C:\**\Program.cs" />`<br /><br /> `</ItemGroup>`<br /><br /> ist der Wert von `%(MyItem.RecursiveDir)` *MySolution\\MyProject\\Source\\*.|  
|%\(Identity\)|Das im `Include`\-Attribut angegebene Element.  Beispiel:<br /><br /> `Source\Program.cs`|  
|%\(ModifiedTime\)|Enthält den Zeitstempel vom Zeitpunkt der letzten Änderung des Elements.  Beispiel:<br /><br /> `2004-07-01 00:21:31.5073316`|  
|%\(CreatedTime\)|Enthält den Zeitstempel vom Zeitpunkt der Erstellung des Elements.  Beispiel:<br /><br /> `2004-06-25 09:26:45.8237425`|  
|%\(AccessedTime\)|Enthält den Zeitstempel vom Zeitpunkt des letzten Zugriffs auf das Element.<br /><br /> `2004-08-14 16:52:36.3168743`|  
  
## Siehe auch  
 [Items](../msbuild/msbuild-items.md)   
 [Batching](../msbuild/msbuild-batching.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)