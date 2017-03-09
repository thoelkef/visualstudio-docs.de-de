---
title: "Unerwartete Typargumente | Microsoft Docs"
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
  - "vbc32088"
  - "bc32088"
helpviewer_keywords: 
  - "BC32088"
ms.assetid: a0918e90-e7ad-4edc-81e1-584e6174bb6c
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Unerwartete Typargumente
Eine `Implements`\-Klausel gibt die Typargumente für den Schnittstellenmember an, der implementiert wird.  
  
 Die `Implements`\-Klausel darf nur die Schnittstelle und den Member identifizieren, der implementiert wird. Wenn Sie also eine generische Prozedur deklarieren, müssen die `Of`\-Klausel und die Typargumente im Hauptteil der Deklaration enthalten sein, wie es auch der Fall ist, wenn keine Schnittstellenprozedur implementiert wird.  
  
 Dieser Fehler kann durch folgenden Code generiert werden.  
  
```  
Public Interface testInterface Sub testSub(Of t)() End Interface Public Class testClass Implements testInterface Public Sub testSub() Implements testInterface.testSub(Of t)() End Sub End Class  
```  
  
 Die Deklaration vor der `Implements`\-Klausel muss wie die Schnittstellendefinition aussehen; Ausnahmen bilden optional hinzugefügte Zugriffs\- oder Prozedurmodifizierer. Mit folgendem Code wird der Fehler vermieden.  
  
```  
Public Sub testSub(Of t)() Implements testInterface.testSub  
```  
  
 **Fehler\-ID:** BC32088  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie die Typargumentliste aus der `Implements`\-Klausel.  
  
-   Wenn Sie einen generischen Member der Schnittstelle implementieren, platzieren Sie die Typargumentliste im Hauptteil der Deklaration vor dem `Implements`\-Schlüsselwort.  
  
## Siehe auch  
 [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause)   
 [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)