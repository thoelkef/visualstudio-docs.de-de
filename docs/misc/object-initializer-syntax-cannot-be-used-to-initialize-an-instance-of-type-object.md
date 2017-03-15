---
title: "Die Syntax des Objektinitialisierers kann nicht zum Initialisieren einer Instanz des Typs &#39;Object&#39; verwendet werden. | Microsoft Docs"
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
  - "bc30994"
  - "vbc30994"
helpviewer_keywords: 
  - "BC30994"
ms.assetid: 2ef65965-f014-4fc1-8c7d-c603f0a764df
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Syntax des Objektinitialisierers kann nicht zum Initialisieren einer Instanz des Typs &#39;Object&#39; verwendet werden.
Eine Instanz von `Object` kann nicht mithilfe der Objektinitialisierersyntax initialisiert werden. Eine Instanz von `Object` enthält keine Eigenschaften oder Felder, denen ein Wert zugewiesen werden kann, und die Objektinitialisierersyntax erfordert mindestens eine entsprechende Eigenschaft oder ein entsprechendes Feld.  
  
```  
' Not valid. ' Dim obj1 = New Object With {} ' Dim obj2 = New Object With {.ToString = <some value>}  
```  
  
 **Fehler\-ID:** BC30994  
  
### So beheben Sie diesen Fehler  
  
1.  Deklarieren Sie Instanzen des Typs `Object` ohne Verwendung einer Initialisiererliste:  
  
    ```  
    Dim obj3 as Object Dim obj4 as New Object()  
    ```  
  
## Siehe auch  
 [Object Initializers: Named and Anonymous Types](../Topic/Object%20Initializers:%20Named%20and%20Anonymous%20Types%20\(Visual%20Basic\).md)   
 [Object Data Type](/dotnet/visual-basic/language-reference/data-types/object-data-type)