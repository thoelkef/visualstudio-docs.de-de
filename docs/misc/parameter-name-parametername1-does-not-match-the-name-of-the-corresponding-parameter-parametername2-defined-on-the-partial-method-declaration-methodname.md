---
title: "Der Parametername &quot;&lt;Parametername1&gt;&quot; stimmt nicht mit dem Namen &quot;&lt;Parametername2&gt;&quot; des entsprechenden Parameters &#252;berein, der f&#252;r die Deklaration der partiellen &lt;Methodenname&gt;-Methode definiert wurde. | Microsoft Docs"
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
  - "vbc31442"
  - "bc31442"
helpviewer_keywords: 
  - "BC31442"
ms.assetid: 7f097bb2-071a-42ec-b7af-40da04f602f2
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Parametername &quot;&lt;Parametername1&gt;&quot; stimmt nicht mit dem Namen &quot;&lt;Parametername2&gt;&quot; des entsprechenden Parameters &#252;berein, der f&#252;r die Deklaration der partiellen &lt;Methodenname&gt;-Methode definiert wurde.
Wenn Parameter für die Deklaration und Implementierung einer partiellen Methode angegeben werden, müssen die Namen der entsprechenden Parameter übereinstimmen. Beispielsweise verursacht der folgende Code diesen Fehler.  
  
```vb#  
Partial Class Product  
  
    ' Declaration of the partial method.  
    Partial Private Sub valueChanged(ByVal newVal As Integer)  
    End Sub  
End Class  
```  
  
```vb#  
Partial Class Product  
  
    ' Implementation of the partial method. This error is  
    ' reported for parameter val.  
    ' Private Sub valueChanged(ByVal val As Integer)  
    '     MsgBox(Value was changed to " & Me.Quantity)  
    ' End Sub  
  
End Class  
```  
  
 **Fehler\-ID:** BC31442  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Parameter oder die Namen in der Deklaration oder in der Implementierung, sodass entsprechende Parameter denselben Namen haben.  
  
## Siehe auch  
 [Partial Methods](/dotnet/visual-basic/programming-guide/language-features/procedures/partial-methods)