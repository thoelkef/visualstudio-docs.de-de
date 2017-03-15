---
title: "&#39;&lt;Methode1&gt;&#39; kann &#39;&lt;Methode2&gt;&#39; nicht &#252;berschreiben, da sie sich durch Standardwerte optionaler Parameter unterscheiden. | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30307"
  - "bc30307"
helpviewer_keywords: 
  - "BC30307"
ms.assetid: c4cf6040-41c3-4650-8eb9-bff063756599
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Methode1&gt;&#39; kann &#39;&lt;Methode2&gt;&#39; nicht &#252;berschreiben, da sie sich durch Standardwerte optionaler Parameter unterscheiden.
Sie haben versucht, eine Methode mit einer anderen Methode zu überschreiben, die sich von der ersten in den Standardwerten ihrer optionalen Parameter unterscheidet, was bedeutet, dass sich ihre Signaturen unterscheiden. Ein Typ kann eine geerbte überschreibbare Methode durch Deklarieren einer Methode mit gleichem Namen und gleicher Signatur überschreiben, die mit dem Modifizierer `Overrides` gekennzeichnet ist.  
  
 **Fehler\-ID:** BC30307  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass die beiden Methoden die gleiche Signatur haben.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [NICHT im BUILD: Überschreiben von Modifizierern](http://msdn.microsoft.com/de-de/18e8ef02-e79b-470e-837a-46a8f4163d32)