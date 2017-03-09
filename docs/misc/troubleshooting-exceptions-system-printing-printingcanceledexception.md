---
title: "Problembehandlung bei Ausnahmen: System.Printing.PrintingCanceledException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "PrintingCanceledException-Ausnahme"
  - "System.Printing.PrintingCanceledException-Ausnahme"
ms.assetid: bec418d6-f168-4a73-962f-5ee0427600b6
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Printing.PrintingCanceledException
Eine <xref:System.Printing.PrintingCanceledException>\-Ausnahme wird ausgelöst, wenn im Code versucht wird, auf einen abgebrochenen Druckauftrag zuzugreifen.  
  
## Hinweise  
 Wenn Sie eine Windows Presentation Foundation \(WPF\)\-Anwendung erstellen, die Druckfunktionen beinhaltet und das Abbrechen von Druckaufträgen gestattet, müssen Sie diese Ausnahme korrekt behandeln. Eine nicht behandelte Ausnahme dieses Typs kann dazu führen, dass eine Windows Presentation Foundation\-Anwendung nicht mehr reagiert.  
  
## Siehe auch  
 <xref:System.Printing.PrintingCanceledException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)