---
title: "Methode &#39;&lt;Methodenname1&gt;&#39; kann die partielle Methode &#39;&lt;Methodenname2&gt;&#39; nicht implementieren, da sie bereits von &#39;&lt;Methodenname3&gt;&#39; implementiert wurde. | Microsoft Docs"
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
  - "vbc31434"
  - "bc31434"
helpviewer_keywords: 
  - "BC31434"
ms.assetid: 61cba19e-db11-4a06-89d6-4244d411588c
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Methode &#39;&lt;Methodenname1&gt;&#39; kann die partielle Methode &#39;&lt;Methodenname2&gt;&#39; nicht implementieren, da sie bereits von &#39;&lt;Methodenname3&gt;&#39; implementiert wurde.
Methode '\<Methodenname1\>' kann die partielle Methode '\<Methodenname2\>' nicht implementieren, da sie bereits von '\<Methodenname3\>' implementiert wurde. Eine partielle Methode kann nur von einer Methode implementiert werden.  
  
 Sie können nicht zwei partielle Methoden verwenden, die dieselbe partielle Methodendeklaration verwenden. Der folgende Code verursacht diesen Fehler.  
  
```vb#  
Partial Class Product ' Declaration of the partial method. Partial Private Sub ValueChanged() End Sub End Class  
```  
  
```vb#  
Partial Class Product ' First implementation of the partial method. Private Sub ValueChanged() MsgBox(Value was changed to " & Me.Quantity) End Sub ' Second implementation of the partial method causes this error. 'Private Sub ValueChanged() '    Console.WriteLine("Quantity was changed to " & Me.Quantity) 'End Sub End Class  
```  
  
 **Fehler\-ID:** BC31434  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)