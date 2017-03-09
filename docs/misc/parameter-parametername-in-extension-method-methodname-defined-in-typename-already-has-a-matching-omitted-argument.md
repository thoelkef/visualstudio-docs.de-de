---
title: "Der Parameter &quot;&lt;Parametername&gt;&quot; in der in &quot;&lt;Typname&gt;&quot; definierten Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; hat bereits ein entsprechendes ausgelassenes Argument. | Microsoft Docs"
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
  - "bc36583"
  - "vbc36583"
helpviewer_keywords: 
  - "BC36583"
ms.assetid: 662072fa-abb8-43c3-8ca2-aefb20f2e902
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Der Parameter &quot;&lt;Parametername&gt;&quot; in der in &quot;&lt;Typname&gt;&quot; definierten Erweiterungsmethode &quot;&lt;Methodenname&gt;&quot; hat bereits ein entsprechendes ausgelassenes Argument.
Bei einem Prozeduraufruf einer Erweiterungsmethode wird ein Argument nach Position ausgelassen und dann anhand des Namens bereitgestellt. Beispiel: Beim folgenden Aufruf der Erweiterungsmethode `ABC` wird zuerst ein Argument für den Parameter `Y` ausgelassen und dann anhand seines Namens bereitgestellt.  
  
```  
<Extension()> _ Public Sub ABC(ByVal X As Integer, Optional ByVal Y As Byte = 0, _ Optional ByVal Z As Byte = 0) End Sub ' . . . ' Calling extension method ABC. Dim number As Integer ' Not valid. ' number.ABC(, 4, Y:=5)  
```  
  
 **Fehler\-ID:** BC36583  
  
### So beheben Sie diesen Fehler  
  
-   Geben Sie das Argument nach Position an, oder entfernen Sie das Komma, durch das es ausgelassen wird.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Passing Arguments by Position and by Name](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-position-and-by-name)