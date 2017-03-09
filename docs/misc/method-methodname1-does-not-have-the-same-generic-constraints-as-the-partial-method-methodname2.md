---
title: "Die &#39;&lt;Methodenname1&gt;&#39;-Methode hat nicht dieselben generischen Einschr&#228;nkungen wie die partielle &#39;&lt;Methodenname2&gt;&#39;-Methode. | Microsoft Docs"
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
  - "bc31438"
  - "vbc31438"
helpviewer_keywords: 
  - "BC31438"
ms.assetid: ea092f0c-661b-49db-80c1-76401fc8bc0b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &#39;&lt;Methodenname1&gt;&#39;-Methode hat nicht dieselben generischen Einschr&#228;nkungen wie die partielle &#39;&lt;Methodenname2&gt;&#39;-Methode.
Sie haben eine partielle Methodenimplementierung definiert, die generische Einschränkungen aufweist, die von den Einschränkungen in der partiellen Methodendeklaration abweichen. Das folgende Codebeispiel veranschaulicht diesen Fehler.  
  
```vb#  
Partial Class Class1 Partial Private Sub Test(Of T As Class)(ByVal arg As T) End Sub End Class Partial Class Class1 '' The error occurs here, for Test. 'Private Sub Test(Of T As Structure)(ByVal arg As T) 'End Sub End Class  
```  
  
 **Fehler\-ID:** BC31438  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)   
 [Generic Procedures in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-procedures)