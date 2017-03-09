---
title: "&#39;&lt;Methode1&gt;&#39; kann &#39;&lt;Methode2&gt;&#39; nicht &#252;berschreiben, da sie sich in den R&#252;ckgabetypen unterscheiden. | Microsoft Docs"
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
  - "bc30437"
  - "vbc30437"
helpviewer_keywords: 
  - "BC30437"
ms.assetid: e566ae72-c597-4b33-b70d-5d4ea879d644
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Methode1&gt;&#39; kann &#39;&lt;Methode2&gt;&#39; nicht &#252;berschreiben, da sie sich in den R&#252;ckgabetypen unterscheiden.
Sie haben versucht, eine Methode mit einer anderen Methode zu überschreiben, die sich durch ihren Rückgabetyp unterscheidet. Ein Typ kann eine geerbte überschreibbare Methode durch Deklarieren einer Methode mit gleichem Namen und gleicher Signatur überschreiben, die mit dem Modifizierer `Overrides` gekennzeichnet ist. Die Signaturen der beiden Methoden müssen übereinstimmen.  
  
 **Fehler\-ID:** BC30437  
  
### So beheben Sie diesen Fehler  
  
-   Überprüfen Sie die Rückgabetypen der beiden Methoden, und ändern Sie sie bei Bedarf, damit sie übereinstimmen.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)