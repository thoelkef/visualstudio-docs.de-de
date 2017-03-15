---
title: "VbStrConv.Wide und VbStrConv.Narrow k&#246;nnen nicht kombiniert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrArgument_IllegalWideNarrow"
ms.assetid: a53b4e6a-36b1-4e36-b2c5-8196313ec599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# VbStrConv.Wide und VbStrConv.Narrow k&#246;nnen nicht kombiniert werden.
Die Anwendung versucht, die sich gegenseitig ausschließenden `VbStrConv`\-Enumerationsmember `Wide` und `Narrow` zu kombinieren.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie entweder `VbStrConv.Wide` oder `VbStrConv.Narrow`.  
  
## Siehe auch  
 <xref:System.Globalization>   
 [NICHT IM BUILD: VbStrConv\-Enumeration](http://msdn.microsoft.com/de-de/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)