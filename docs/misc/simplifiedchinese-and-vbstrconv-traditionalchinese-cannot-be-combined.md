---
title: "SimplifiedChinese und VbStrConv.TraditionalChinese k&#246;nnen nicht kombiniert werden. | Microsoft Docs"
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
  - "vbrArgument_StrConvSCandTC"
ms.assetid: d8e6a11b-f549-43b5-8337-0594340e1325
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# SimplifiedChinese und VbStrConv.TraditionalChinese k&#246;nnen nicht kombiniert werden.
Die Anwendung versucht, die sich gegenseitig ausschließenden `VbStrConv`\-Enumerationsmember `SimplifiedChinese` und `TraditionalChinese` zu kombinieren.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie entweder  `VbStrConv.SimplifiedChinese` oder `VbStrConv.TraditionalChinese`.  
  
## Siehe auch  
 <xref:System.Globalization>   
 [NICHT IM BUILD: VbStrConv\-Enumeration](http://msdn.microsoft.com/de-de/59f83dd9-6361-47df-a836-02ba9d4cb936)   
 [Einführung in internationale Anwendungen basierend auf .NET Framework](../ide/introduction-to-international-applications-based-on-the-dotnet-framework.md)