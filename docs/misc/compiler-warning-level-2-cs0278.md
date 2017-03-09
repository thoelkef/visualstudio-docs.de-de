---
title: "Compilerwarnung (Stufe 2) CS0278 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0278"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0278"
ms.assetid: 5418cbbe-bcec-4379-a6f6-410987beb96a
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0278
"Typ" implementiert das Muster "Mustername" nicht. "Methodenname" unterscheidet sich nicht eindeutig von "Methodenname".  
  
 Es gibt mehrere Anweisungen in C\#, die auf definierten Muster aufsetzen, etwa `foreach` und `using`. Beispielsweise setzt `foreach` auf der Auflistungsklasse auf, die das „enumerable“\-Muster implementiert.  
  
 CS0278 kann auftreten, wenn der Compiler den Abgleich aufgrund von Mehrdeutigkeiten nicht vornehmen kann. Beispielsweise erfordert das „enumerable“\-Muster, dass es eine Methode namens `MoveNext` gibt, und der Code enthält möglicherweise zwei Methoden namens `MoveNext`. Der Compiler versucht, die zu verwendende Schnittstelle zu finden, aber es wird empfohlen, dass Sie die Ursache für die Mehrdeutigkeit ermitteln und diese beheben.  
  
 Weitere Informationen finden Sie unter [Gewusst wie: Zugreifen auf Auflistungsklassen mit foreach](../Topic/How%20to:%20Access%20a%20Collection%20Class%20with%20foreach%20\(C%23%20Programming%20Guide\).md).  
  
## Beispiel  
 Im folgenden Beispiel wird CS0278 generiert:  
  
```  
// CS0278.cs using System.Collections.Generic; public class myTest { public static void TestForeach<W>(W w) where W: IEnumerable<int>, IEnumerable<string> { foreach (int i in w) {}   // CS0278 } }  
```