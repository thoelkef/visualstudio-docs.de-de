---
title: "Es kann kein gemeinsamer Typ f&#252;r den ersten und zweiten Operanden des bin&#228;ren If-Operators abgeleitet werden. | Microsoft Docs"
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
  - "vbc33110"
  - "bc33110"
helpviewer_keywords: 
  - "BC33110"
ms.assetid: f46873aa-f6cd-4cc9-9e8e-e668bddf0980
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Es kann kein gemeinsamer Typ f&#252;r den ersten und zweiten Operanden des bin&#228;ren If-Operators abgeleitet werden.
Es kann kein gemeinsamer Typ für den ersten und zweiten Operanden des binären If\-Operators abgeleitet werden. Für einen muss eine erweiternde Konvertierung in den anderen durchgeführt werden.  
  
 Der binäre `If`\-Operator erfordert, dass zwischen einem der Argumente und dem anderen Argument eine erweiternde Konvertierung erfolgt. Da z. B. zwischen `Integer` und `String` in beide Richtungen keine erweiternde Konvertierung durchgeführt wird, verursacht folgender Code diesen Fehler.  
  
```vb#  
Dim first? As Integer  
Dim second As String = "First is Nothing"  
'' Not valid.  
' Console.WriteLine(If(first, second))  
```  
  
 **Fehler\-ID:** BC33110  
  
### So beheben Sie diesen Fehler  
  
-   Stellen Sie eine explizite Konvertierung für einen der Operanden bereit, wenn dies in Ihrem Code möglich ist:  
  
    ```  
    Console.WriteLine(If(first, CInt(second)))   
    ```  
  
-   Verwenden eine andere bedingte Konstruktion, um den Code neu zu schreiben.  
  
    ```  
    If first IsNot Nothing Then  
        Console.WriteLine(first)  
    Else  
        Console.WriteLine(second)  
    End If  
    ```  
  
## Siehe auch  
 [If Operator](/dotnet/visual-basic/language-reference/operators/if-operator)   
 [Widening and Narrowing Conversions](/dotnet/visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions)   
 [If...Then...Else Statement](/dotnet/visual-basic/language-reference/statements/if-then-else-statement)