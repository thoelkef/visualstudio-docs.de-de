---
title: "Unable to retrieve resource information | Microsoft Docs"
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
  - "vs.tasklisterror.resx_scan_failed"
ms.assetid: e4389ff0-eb64-4c31-b32f-5216c73fadfb
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Unable to retrieve resource information
Fehler bei Suche nach RESX\-Dateien in der Hierarchie.  
  
 Als Teil des Buildschritts `Preparing resources`, der im **Ausgabefenster** angezeigt wird, durchsucht das Projektsystem die Projekthierarchie nach allen Dateien mit einer RESX\-Erweiterung.  Dadurch wird eine Liste der RESX\-XML\-Dateien erstellt, die in binäre Ressourcendateien umgewandelt werden müssen, bevor sie als Ressourcen in die Projektausgabe eingefügt werden können.  
  
 **So beheben Sie diesen Fehler**  
  
-   Starten Sie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] neu.  Wenn es immer noch nicht funktioniert, wenden Sie sich mit diesem Problem an den Microsoft\-Produktsupport.  
  
     Durch diesen Fehler schlägt das Build fehl.  
  
## Siehe auch  
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/de-de/f793852c-da06-4d52-a826-65f635844772)