---
title: "Die Erstellungsausgaben konnten nicht in das Web kopiert werden | Microsoft Docs"
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
  - "vs.tasklisterror.cantcopyoutputstoweb"
ms.assetid: 59cf714b-cf7d-4df9-81ae-d3254969d5bc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Die Erstellungsausgaben konnten nicht in das Web kopiert werden
Das Projektsystem konnte mindestens eine Buildausgabedatei \(z. B. die erstellte DLL oder PDB oder die erstellten Satellitenassemblys\) nicht auf den Webserver kopieren.  
  
 Diese Fehlermeldung gibt an, dass mindestens eine Buildausgabedatei nicht auf den Webserver kopiert wurde.  
  
 In den meisten Fällen wird dieser Fehler dadurch verursacht, dass eine Ausgabedatei des Builds auf dem Server schreibgeschützt oder gesperrt ist. Ist eine Datei auf dem Server gesperrt, ist dies ein Hinweis darauf, dass die aktuell auf dem Server verfügbaren Assemblys, Satelliten oder Debugsymbole von der [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Runtime nicht ordnungsgemäß kopiert wurden.  
  
 Außerdem kann der Fehler dadurch verursacht sein, dass die Speicherkapazität des Servers nicht ausreicht oder dass [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Dateien aufgrund von Netzwerkproblemen nicht auf den Webserver hochladen kann.  
  
### So beheben Sie diesen Fehler  
  
1.  Prüfen Sie den Speicherplatz.  
  
2.  Wenn eine Datei gesperrt ist, starten Sie den Webserver neu, um die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Sperre der betroffenen Datei\(en\) aufzuheben.  
  
## Siehe auch  
 [PDB Files](http://msdn.microsoft.com/de-de/1761c84e-8c2c-4632-9649-b5f99964ed3f)