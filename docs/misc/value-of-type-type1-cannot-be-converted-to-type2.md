---
title: "Der Wert vom Typ &#39;&lt;Typ1&gt;&#39; kann nicht zu &#39;&lt;Typ2&gt;&#39; konvertiert werden | Microsoft Docs"
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
  - "bc30311"
  - "vbc30311"
helpviewer_keywords: 
  - "BC30311"
ms.assetid: e3a513d4-2a1e-46d6-b592-b2e756b89d7d
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Wert vom Typ &#39;&lt;Typ1&gt;&#39; kann nicht zu &#39;&lt;Typ2&gt;&#39; konvertiert werden
Eine Anweisung versucht, einen Datentyp auf eine nicht definierte Weise in einen anderen Datentyp zu konvertieren. Dieser Fehler kann u. a. folgende Ursachen haben:  
  
-   Eine Konvertierung gibt zwei Datentypen an, zwischen denen keine Konvertierung möglich ist. Ein Beispiel hierfür ist eine Konvertierung eines `Boolean`\-Werts in den `Date`\-Typ.  
  
-   Eine Initialisierung eines Arrays umfasst im Anschluss an eine `New`\-Klausel keine geschweiften Klammern \(`{}`\). In diesem Fall hat \<Typ2\> das Format '1\-dimensionales Array von \<Typ\>'.  
  
 **Fehler\-ID:** BC30311  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie sicher, dass der Ausdruck in den Zieldatentyp konvertiert werden kann.  
  
-   Wenn \<Typ2\> ein Array ist, vergewissern Sie sich, dass die `New`\-Klausel im Anschluss an den Typnamen sowohl eckige als auch geschweifte Klammern enthält. Der folgende Code zeigt die korrekte Initialisierung eines Arrays.  
  
    ```  
    Dim anIntArray As Integer() = New Integer() {}  
    ```  
  
## Siehe auch  
 [Type Conversions in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/type-conversions)   
 [How to: Initialize an Array Variable in Visual Basic](../Topic/How%20to:%20Initialize%20an%20Array%20Variable%20in%20Visual%20Basic.md)