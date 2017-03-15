---
title: "Das Argument &#39;Period&#39; muss kleiner als oder gleich gro&#223; wie das Argument &#39;Life&#39; sein | Microsoft Docs"
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
  - "vbrFinancial_PeriodLELife"
ms.assetid: dc575d41-b376-4b05-bbbe-6de1e98385f1
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das Argument &#39;Period&#39; muss kleiner als oder gleich gro&#223; wie das Argument &#39;Life&#39; sein
Der Wert des `Period`\-Arguments, das den Zeitraum angibt, für den das Veralten von Ressourcen berechnet wird, ist größer als der Wert des `Life`\-Arguments.  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die Argumente `Life` und `Period` in den gleichen Einheiten ausgedrückt werden. Wenn beispielsweise `Life` in Monaten gemessen wird, sollte das auch auf `Period` zutreffen.  
  
## Siehe auch  
 [NICHT IM BUILD: DDB\-Funktion](http://msdn.microsoft.com/de-de/c7cf8929-d158-4399-b3cb-31d897d12556)   
 [NICHT IM BUILD: SYD\-Funktion](http://msdn.microsoft.com/de-de/23c25672-f5dd-49ac-9893-4faa82634181)   
 [Passing Arguments by Value and by Reference](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference)