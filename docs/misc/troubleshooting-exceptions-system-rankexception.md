---
title: "Problembehandlung bei Ausnahmen: System.RankException | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
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
  - "RankException-Klasse"
ms.assetid: ad7aa34a-f84b-4650-aaec-a75a8b85c50f
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Problembehandlung bei Ausnahmen: System.RankException
Eine <xref:System.RankException>\-Ausnahme wird ausgelöst, wenn ein Array mit der falschen Anzahl von Dimensionen an eine Methode übergeben wird.  
  
## Tipps  
 **Stellen Sie sicher, dass das Array die erforderliche Anzahl von Dimensionen aufweist.**  
 Visual Basic\-Benutzer finden weitere Informationen unter [Array Dimensions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/arrays/array-dimensions).  
  
 C\#\-Benutzer finden weitere Informationen unter [Arrays](/dotnet/csharp/programming-guide/arrays/index).  
  
## Hinweise  
 Da Arrayfeldindizes bei 0 beginnen, ist der niedrigste mögliche Feldindex für eine Dimension immer 0.  
  
## Siehe auch  
 <xref:System.RankException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)   
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)