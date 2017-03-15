---
title: "&quot;&lt;Prozedurname1&gt;&quot; kann &quot;&lt;Prozedurname2&gt;&quot; nicht &#252;berschreiben, da sie sich durch Parameter unterscheiden, die als ParamArray deklariert sind. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30906"
  - "vbc30906"
helpviewer_keywords: 
  - "BC30906"
ms.assetid: 12939030-732e-4c6d-8fe9-707b7532174b
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Prozedurname1&gt;&quot; kann &quot;&lt;Prozedurname2&gt;&quot; nicht &#252;berschreiben, da sie sich durch Parameter unterscheiden, die als ParamArray deklariert sind.
Eine Prozedur in einer abgeleiteten Klasse überschreibt eine Prozedur gleichen Namens in der Basisklasse, aber die Parameterlisten unterscheiden sich.  
  
 Um eine Prozedur in einer geerbten Klasse zu überschreiben, müssen Parameterliste, Zugriffsebene und Rückgabetyp \(sofern vorhanden\) der überschreibenden Prozedur übereinstimmen. Insbesondere müssen alle [Optional](/dotnet/visual-basic/language-reference/modifiers/optional)\- oder [ParamArray](/dotnet/visual-basic/language-reference/modifiers/paramarray)\-Deklarationen übereinstimmen.  
  
 **Fehler\-ID:** BC30906  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie die Prozedur überschreiben möchten, sorgen Sie dafür, dass die Parameterliste exakt der Parameterliste in der Basisklassenprozedur entspricht. Wenn der letzte Parameter in der Basisklassenprozedur mit `ParamArray` deklariert ist, muss er auch in der überschreibenden Prozedur mit `ParamArray` deklariert sein.  
  
-   Wenn sich die Parameterliste von der Basisklassenversion unterscheiden soll, können Sie sie nicht überschreiben. Ziehen Sie stattdessen eine Überladung in Betracht. Weitere Informationen finden Sie unter [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading).  
  
## Siehe auch  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [NICHT IM BUILD: Überschreiben von Eigenschaften und Methoden](http://msdn.microsoft.com/de-de/2167e8f5-1225-4b13-9ebd-02591ba90213)