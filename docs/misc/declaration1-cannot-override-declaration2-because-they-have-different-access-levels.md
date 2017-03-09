---
title: "&quot;&lt;Deklaration1&gt;&quot; kann &quot;&lt;Deklaration2&gt;&quot; nicht &#252;berschreiben, weil sie unterschiedliche Zugriffsebenen haben | Microsoft Docs"
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
  - "bc30266"
  - "vbc30266"
helpviewer_keywords: 
  - "BC30266"
ms.assetid: c9c5c14e-876c-430d-ab98-5087c19efae7
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Deklaration1&gt;&quot; kann &quot;&lt;Deklaration2&gt;&quot; nicht &#252;berschreiben, weil sie unterschiedliche Zugriffsebenen haben
Eine Prozedur oder Eigenschaftendeklaration versucht, ein geerbtes Element mit demselben Namen zu überschreiben. Allerdings gibt sie einen anderen Zugriff als das geerbte Element an. Die Zugriffsebene des geerbten Elements \(z. B. `Public` oder `Private`\) muss beim Überschreiben beibehalten werden.  
  
 **Fehler\-ID:** BC30266  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Zugriff des überschreibenden Elements, damit er mit dem Zugriff des geerbten Elements übereinstimmt.  
  
## Siehe auch  
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)   
 [Access Levels in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/declared-elements/access-levels)