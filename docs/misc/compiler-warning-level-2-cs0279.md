---
title: "Compilerwarnung (Stufe 2) CS0279 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0279"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0279"
ms.assetid: 5e5faa8f-3d5b-4999-aa62-ff7f131a3e04
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 2) CS0279
'Typname' implementiert das Muster 'Mustername' nicht. 'Methodenname' ist entweder statisch oder nicht öffentlich.  
  
 Es gibt mehrere Anweisungen in C\#, die auf definierten Muster aufsetzen, z. B. `foreach` und `using`. Beispielsweise setzt `foreach` auf der Auflistungsklasse auf, die das „enumerable“\-Muster implementiert. Dieser Fehler tritt auf, wenn der Compiler den Abgleich aufgrund einer Methode, die als `static` oder nicht `public` deklariert ist, nicht vornehmen kann. Methoden in Mustern müssen Instanzen von Klassen und öffentlich sein.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0279 generiert:  
  
```  
// CS0279.cs using System; using System.Collections; public class myTest : IEnumerable { IEnumerator IEnumerable.GetEnumerator() { yield return 0; } internal IEnumerator GetEnumerator() { yield return 0; } public static void Main() { foreach (int i in new myTest()) {}  // CS0279 } }  
```