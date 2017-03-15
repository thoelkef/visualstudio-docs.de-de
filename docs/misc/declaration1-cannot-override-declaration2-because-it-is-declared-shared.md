---
title: "&quot;&lt;Deklaration1&gt;&quot; kann &quot;&lt;Deklaration2&gt;&quot; nicht &#252;berschreiben, da diese als &quot;Shared&quot; deklariert ist. | Microsoft Docs"
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
  - "vbc30268"
  - "bc30268"
helpviewer_keywords: 
  - "BC30268"
ms.assetid: d011fb26-6236-462e-9173-622f8bbeb536
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Deklaration1&gt;&quot; kann &quot;&lt;Deklaration2&gt;&quot; nicht &#252;berschreiben, da diese als &quot;Shared&quot; deklariert ist.
Eine Prozedur oder Eigenschaftendeklaration versucht, ein geerbtes Element mit demselben Namen zu überschreiben. Das geerbte Element ist jedoch als `Shared` deklariert. Als "Shared" deklarierte Elemente werden nicht mit einer Instanz der Klasse verknüpft. Daher können sie nicht überschrieben werden.  
  
 **Fehler\-ID:** BC30268  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Shared`\-Schlüsselwort aus dem geerbten Element, oder entfernen Sie die überschreibende Deklaration.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)