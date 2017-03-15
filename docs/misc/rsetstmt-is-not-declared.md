---
title: "&quot;&lt;rsetstmt&gt;&quot; ist nicht deklariert | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30821"
  - "vbc30821"
helpviewer_keywords: 
  - "BC30821"
ms.assetid: 7936e3ef-7ac6-4a71-af55-acc2c5cd8754
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;rsetstmt&gt;&quot; ist nicht deklariert
"\<rsetstmt\>" ist nicht deklariert. RSet\-Anweisungen werden nicht mehr unterstützt. Verwenden Sie stattdessen Microsoft.VisualBasic.RSet.  
  
 Einige systeminterne Funktionen von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] in früheren Versionen wurden in den <xref:Microsoft.VisualBasic?displayProperty=fullName>\-Namespace verschoben. Dadurch wird ihre Funktionalität allgemeiner verfügbar für alle Programmiersprachen.  
  
 **Fehler\-ID:** BC30821  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie stattdessen die `RSet`\-Funktion im `Microsoft.VisualBasic`\-Namespace.  
  
## Siehe auch  
 [NICHT IM BUILD: RSet\-Funktion](http://msdn.microsoft.com/de-de/534514e5-dee9-4dfd-993b-da09731eece5)   
 [Programming Element Support Changes Summary](http://msdn.microsoft.com/de-de/0483590a-6309-449c-a2fa-effa26a03b95)