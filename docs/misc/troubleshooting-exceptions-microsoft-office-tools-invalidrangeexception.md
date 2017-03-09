---
title: "Problembehandlung bei Ausnahmen: Microsoft.Office.Tools.InvalidRangeException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
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
  - "Microsoft.Office.Tools.InvalidRangeException-Ausnahme"
ms.assetid: 0deea25b-1152-40b6-89e2-e2e9c85f7dc0
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: Microsoft.Office.Tools.InvalidRangeException
Eine <xref:Microsoft.Office.Tools.InvalidRangeException>\-Ausnahme wird ausgelöst, wenn ein Ansichtssteuerelement programmgesteuert erstellt wird, dessen Bereich sich über mehrere Zonen erstreckt.  
  
## Tipps  
 Stellen Sie sicher, dass die vom Bereich bedeckte Zone sich mit keinem anderen Bereich überschneidet.  
 Bereiche dürfen sich nicht überschneiden.  
  
 Stellen Sie sicher, dass programmgesteuert erstellte Ansichtssteuerelemente nur eine einzelne Zone umfassen.  
 -   Stellen Sie sicher, dass programmgesteuert erstellte Ansichtssteuerelemente nur eine einzelne Zone umfassen, d. h. dass alle Zellen in Verbindung sind.  
  
## Siehe auch  
 <xref:Microsoft.Office.Tools.InvalidRangeException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)