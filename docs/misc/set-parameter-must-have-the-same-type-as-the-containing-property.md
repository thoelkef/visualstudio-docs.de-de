---
title: "Der Set-Parameter muss denselben Typ wie die Eigenschaft haben, in der er sich befindet. | Microsoft Docs"
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
  - "vbc31064"
  - "bc31064"
helpviewer_keywords: 
  - "BC31064"
ms.assetid: f0b8310d-68a1-4989-ac64-03b1861528ad
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Set-Parameter muss denselben Typ wie die Eigenschaft haben, in der er sich befindet.
Der Parameter für die `Set`\-Eigenschaftenprozedur weist einen anderen Typ als die Eigenschaft auf, zu der er gehört.  
  
 **Fehler\-ID:** BC31064  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Datentyp des Parameters in `Set`, damit er mit dem Datentyp der Eigenschaft übereinstimmt. Zum Beispiel:  
  
    ```  
    Class Class1 ' Declare a local variable to hold the property value. Private Fval As Integer Property F() As Integer Get Return Fval End Get Set(ByVal Value As Integer) Fval = Value End Set End Property End Class  
    ```  
  
## Siehe auch  
 [NICHT IM BUILD: Gewusst wie: Hinzufügen von Feldern und Eigenschaften zu einer Klasse](http://msdn.microsoft.com/de-de/ae53f61b-3abc-413e-8931-703c5f5e8fc2)   
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [NICHT IM BUILD: Eigenschaften und Eigenschaftenprozeduren](http://msdn.microsoft.com/de-de/23e2a1ec-7e9d-4109-8940-c703d981077b)