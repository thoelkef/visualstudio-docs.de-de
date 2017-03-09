---
title: "&#39;&lt;Deklaration1&gt;&#39; kann &#39;&lt;Deklaration2&gt;&#39; nicht &#252;berschreiben, da diese als &#39;NotOverridable&#39; deklariert ist. | Microsoft Docs"
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
  - "bc30267"
  - "vbc30267"
helpviewer_keywords: 
  - "BC30267"
ms.assetid: fb1f6797-4e49-442e-a660-59d602132631
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;Deklaration1&gt;&#39; kann &#39;&lt;Deklaration2&gt;&#39; nicht &#252;berschreiben, da diese als &#39;NotOverridable&#39; deklariert ist.
Eine Prozedur oder Eigenschaftendeklaration versucht, ein geerbtes Element mit demselben Namen zu überschreiben. Das geerbte Element ist jedoch als `NotOverridable` deklariert.  
  
 **Fehler\-ID:** BC30267  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `NotOverridable`\-Schlüsselwort aus der Deklaration des geerbten Elements, oder entfernen Sie die überschreibende Deklaration.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)