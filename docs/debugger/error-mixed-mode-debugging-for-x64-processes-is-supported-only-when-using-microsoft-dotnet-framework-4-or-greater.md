---
title: "Fehler: Debuggen im gemischten Modus f&#252;r x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder h&#246;her, unterst&#252;tzt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.interop_unsupported_x64"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: e4b0216c-7006-4832-883f-08e982ba8d3f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Fehler: Debuggen im gemischten Modus f&#252;r x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder h&#246;her, unterst&#252;tzt
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Um gemischten systemeigenen und verwalteten Code in einem 64\-Bit\-Prozess zu debuggen, benötigen Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4.  Das Debuggen von 64\-Bit\-Prozessen im gemischten Modus wird erst ab [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 unterstützt.  
  
### So beheben Sie diesen Fehler  
  
-   Führen Sie einen der folgenden Schritte aus:  
  
    -   Aktualisieren Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] auf Version 4.  
  
    -   Erstellen Sie eine 32\-Bit\-Version der Anwendung zum Debuggen.  
  
## Siehe auch  
 [Einrichten der Remotetools auf dem Gerät](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md)