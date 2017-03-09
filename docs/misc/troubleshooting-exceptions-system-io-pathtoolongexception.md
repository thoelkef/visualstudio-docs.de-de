---
title: "Problembehandlung bei Ausnahmen: System.IO.PathTooLongException | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "PathTooLongException-Klasse"
ms.assetid: 8912c425-bf91-42e3-82d8-bee6b2062db3
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.IO.PathTooLongException
Eine <xref:System.IO.PathTooLongException>\-Ausnahme wird ausgelöst, wenn ein Pfadname oder ein Dateiname die vom System definierte maximale Länge übersteigt.  
  
## Tipps  
 **Stellen Sie sicher, dass der Pfad nicht länger als das vom System vorgegebene Maximum ist.**  
 Auf Windows\-basierten Plattformen dürfen Pfade nicht länger als 247 Zeichen und Dateinamen nicht länger als 259 Zeichen sein.  
  
## Siehe auch  
 <xref:System.IO.PathTooLongException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Gewusst wie: Analysieren von Dateipfaden](../Topic/How%20to:%20Parse%20File%20Paths%20in%20Visual%20Basic.md)