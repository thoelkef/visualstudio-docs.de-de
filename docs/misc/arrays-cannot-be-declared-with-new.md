---
title: "Arrays k&#246;nnen nicht mit &#39;New&#39; deklariert werden | Microsoft Docs"
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
  - "vbc30053"
  - "bc30053"
helpviewer_keywords: 
  - "BC30053"
ms.assetid: aa55f3b7-2045-497b-9543-5ec6e2b74fe2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Arrays k&#246;nnen nicht mit &#39;New&#39; deklariert werden
Das Schlüsselwort `New` kann nur im Initialisierungsteil einer Arraydeklaration auftreten. Dies bedeutet, dass sich `New` auf der rechten Seite des Gleichheitszeichens \(`=`\) befinden muss, damit ein neuer Arraytyp erstellt werden kann, der der Arrayvariablen zugewiesen werden kann.  
  
 Das abgekürzte Verfahren für die Klasseninitialisierung ist für Arrays nicht verfügbar. Die folgenden beiden Codezeilen sind gültig und gleichwertig, weil sie ein Objekt aus einer Klasse initialisieren.  
  
```  
Dim formA as Form = New Form Dim formA as New Form  
```  
  
 Allerdings kann die Arrayinitialisierung nicht das gleiche abgekürzte Verfahren wie die Klasseninitialisierung verwenden.  
  
 Beachten Sie, dass die `New`\-Klausel für ein Array runde Klammern \(`()`\) und geschweifte Klammern \(`{}`\) enthalten muss. Die runden Klammern geben an, dass der neue Typ ein Array ist, und die geschweiften Klammern stellen die Initialisierungswerte bereit. Der Compiler benötigt die geschweiften Klammern selbst dann, wenn sie leer sind – also auch dann, wenn Sie keinen der Arraywerte initialisieren.  
  
 **Fehler\-ID:** BC30053  
  
### So beheben Sie diesen Fehler  
  
-   Ersetzen Sie z. B. eine Anweisung wie `Dim myDates() As New Date`\) durch eine Anweisung wie `Dim myDates() As Date = New Date() {}`.  
  
## Siehe auch  
 [Arrays](/dotnet/visual-basic/programming-guide/language-features/arrays/index)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)