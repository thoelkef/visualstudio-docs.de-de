---
title: "System DLL &lt;name&gt; could not be loaded. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.message.VB_E_TERRSYSDLLNOTLOADED"
  - "vs.message.0x800A0085"
ms.assetid: d4ccb3b1-fbc3-4395-a9b1-be50a4d7bf44
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# System DLL &lt;name&gt; could not be loaded.
Eine vom Betriebssystem bereitgestellte DLL\-Datei wie **DDEML.DLL**, **VERSION.DLL** oder **WINSPOOL.DRV** konnte nicht gefunden werden.  Im Allgemeinen tritt dieser Fehler auf, wenn einer der folgenden Umstände vorliegt: Die Datei befindet sich nicht im richtigen Pfad, die DLL ist beschädigt oder wurde gelöscht, oder es ist nicht genügend Arbeitsspeicher vorhanden.  
  
### So beheben Sie diesen Fehler  
  
1.  Stellen Sie sicher, dass sich die DLL im Windows\-Systempfad befindet.  
  
     \- oder \-  
  
     Laden Sie die DLL neu.  
  
     \- oder \-  
  
     Geben Sie Speicherplatz frei, indem Sie andere geöffnete Anwendungen schließen.