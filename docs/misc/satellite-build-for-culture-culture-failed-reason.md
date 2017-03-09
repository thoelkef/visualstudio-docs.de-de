---
title: "Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.satellite_build_failed"
ms.assetid: c97c589f-cf4d-4f6b-941a-7526a1091fce
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Satellite build for culture &#39;culture&#39; failed. &lt;reason&gt;
Eine Satellitenassembly konnte für eine bestimmte Kultur nicht erstellt werden.  Durch diesen Fehler schlägt der Buildprozess fehl.  
  
 Dieser Fehler kann zwei Ursachen haben:  
  
1.  **ALINK.EXE** ist nicht auf dem System installiert.  
  
2.  **ALINK.EXE** ist fehlgeschlagen, hat jedoch keine detaillierten Fehlerinformationen zurückgegeben.  
  
 **So beheben Sie diesen Fehler**  
  
-   Installieren Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] oder lediglich [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] neu.  
  
-   Wenn als \<Ursache\> die Meldung "Der Assemblylinker konnte nicht gestartet werden.  Die Datei ist vorhanden" angezeigt wird, leeren Sie den Temp\-Ordner, in dem die Dateien generiert werden \(z. B. C:\\Dokumente und Einstellungen\\\<Benutzername\>\\Lokale Einstellungen\\Temp\).  
  
## Siehe auch  
 [Al.exe \(Assembly Linker\-Tool\)](../Topic/Al.exe%20\(Assembly%20Linker\).md)