---
title: "Die Erweiterungsmethode &#39;&lt;Methodenname&gt;&#39; verf&#252;gt &#252;ber Typeinschr&#228;nkungen, die nie erf&#252;llt werden. | Microsoft Docs"
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
  - "bc36561"
  - "vbc36561"
helpviewer_keywords: 
  - "BC36561"
ms.assetid: ff42d6e9-611b-407d-a269-f268b36ed277
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die Erweiterungsmethode &#39;&lt;Methodenname&gt;&#39; verf&#252;gt &#252;ber Typeinschr&#228;nkungen, die nie erf&#252;llt werden.
Die Typparameter dieser Methode interagieren auf eine Weise, die verhindert, dass sie jemals erfüllt werden. Die folgende Erweiterungsmethode ist ein Beispiel.  
  
```  
'' Not valid. '<Extension()> _ 'Sub extensionExample(Of T As U, U)(ByVal para1 As T, ByVal para2 As U) 'End Sub  
```  
  
 Da die Methode eine Erweiterungsmethode ist, muss der Compiler den Datentyp bzw. die Datentypen, die von der Methode erweitert werden, auf Basis des ersten Parameters in der Methodendeklaration, `para1`, und des Arguments bestimmen können, das für diesen Parameter gesendet wird. Wenn der erste Parameter auf die generischen Typparameter \(`para1 as T`\) verweist, schränken die Einschränkungen für generische Parameter den Satz von Typen ein, auf den die Methode angewendet wird.  
  
 Die Anwendbarkeit einer Erweiterungsmethode wird über das Argument bestimmt, das für den ersten Parameter bereitgestellt wird, bei dem es sich im folgenden Code um `arg1` handelt.  
  
 `'' Not valid.`  
  
 `'arg1.extensionExample(arg2)`  
  
 Es muss möglich sein, die Einschränkungen für alle generischen Typparameter zu überprüfen, auf die vom ersten Parameter \(`para1`\) verwiesen wird, indem nur das erste Argument \( `arg1`\) betrachtet wird. In `extensionExample` kann der zu erweiternde Satz von Typen nicht allein über den ersten Parameter ermittelt werden. Der Typparameter `T` wird durch den Typparameter `U` eingeschränkt, auf den `para1` nicht verweist und der nicht von `arg1` abgeleitet werden kann. Aus diesem Grund kann die Anwendbarkeit der Methode auf alle möglichen Typen nicht überprüft werden, und die Methode kann nie aufgerufen werden.  
  
 **Fehler\-ID:** BC36561  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Typdeklaration, um die wechselseitige Abhängigkeit zwischen den Typen zu entfernen.  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)