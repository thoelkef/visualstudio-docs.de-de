---
title: "Die Typeinschr&#228;nkung &quot;&lt;Ausdruck&gt;&quot; ist keine Klasse oder Schnittstelle. | Microsoft Docs"
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
  - "bc32048"
  - "vbc32048"
helpviewer_keywords: 
  - "BC32048"
ms.assetid: 68811886-44ac-43e1-9315-b39857310033
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Typeinschr&#228;nkung &quot;&lt;Ausdruck&gt;&quot; ist keine Klasse oder Schnittstelle.
Eine Einschränkungsliste enthält einen Ausdruck, der keine gültige Einschränkung für einen Typparameter darstellt.  
  
 Eine Einschränkungsliste erzwingt Anforderungen an das Typargument, das an den Typparameter übergeben wird. Sie können die folgenden Anforderungen in beliebiger Kombination angeben:  
  
-   Das Typargument muss mindestens eine Schnittstelle implementieren.  
  
-   Das Typargument darf von höchstens einer Klasse erben.  
  
-   Das Typargument muss einen parameterlosen Konstruktor verfügbar machen, auf den der erstellende Code zugreifen kann.  
  
-   Das Typargument muss ein Verweistyp oder Werttyp sein.  
  
 **Fehler\-ID:** BC32048  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass der Ausdruck und dessen Elemente richtig geschrieben sind.  
  
-   Wenn der Ausdruck die Anforderungen der vorangehenden Liste nicht erfüllt, entfernen Sie ihn aus der Einschränkungsliste.  
  
-   Wenn der Ausdruck auf eine Schnittstelle oder Klasse verweist, stellen Sie sicher, dass der Compiler Zugriff auf diese Schnittstelle oder Klasse hat. Möglicherweise müssen Sie deren Namen qualifizieren und einen Verweis auf Ihr Projekt hinzufügen. Weitere Informationen finden Sie unter "Verweise auf Projekte" in [NOTINBUILD: Auflösen eines Verweises bei mehreren Variablen mit gleichem Namen](http://msdn.microsoft.com/de-de/9601e39f-1911-44e1-ace5-3f6e090408b9).  
  
## Siehe auch  
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Value Types and Reference Types](/dotnet/visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types)   
 [NOTINBUILD Gewusst wie: Qualifizieren eines deklarierten Elementnamens](http://msdn.microsoft.com/de-de/6bd112f5-df6f-42b8-9427-a9225bfcbaab)   
 [How to: Add and Remove Project References](http://msdn.microsoft.com/de-de/f51b784d-0bc8-4c19-a898-e560d5ed696b)