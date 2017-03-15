---
title: "Problembehandlung bei Ausnahmen: System.Windows.Xps.XpsWriterException | Microsoft Docs"
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
  - "EHWXXpsWriter"
helpviewer_keywords: 
  - "System.Windows.Xps.XpsWriterException-Ausnahme"
  - "XpsWriterException-Ausnahme"
ms.assetid: 3b9fbb94-ed67-44f2-82bb-af5cb5ada1ef
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.Windows.Xps.XpsWriterException
Eine <xref:System.Windows.Xps.XpsWriterException>\-Ausnahme wird ausgelöst, wenn eine Methode eines <xref:System.Windows.Xps.XpsDocumentWriter>\-Objekts oder eines <xref:System.Windows.Xps.VisualsToXpsDocument>\-Objekts aufgerufen wird, die mit dem aktuellen Status des Objekts nicht kompatibel ist.  
  
## Hinweise  
 Diese Ausnahme wird z. B. ausgelöst, wenn die `CancelAsync`\-Methode eines der Objekttypen aufgerufen wird, wenn das Objekt keinen asynchronen Schreibvorgang ausführt.  
  
## Siehe auch  
 <xref:System.Windows.Xps.XpsWriterException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)