---
title: "Compilerfehler CS1913 | Microsoft Docs"
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
  - "CS1913"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1913"
ms.assetid: 652494b3-9576-4a4c-a9ee-695f86c4a023
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1913
Der Member "Name" kann nicht initialisiert werden. Er ist kein Feld und keine Eigenschaft.  
  
 Objektinitialisierer können nur verwendet werden, um verfügbare Felder oder Eigenschaften zu initialisieren.  
  
### So beheben Sie diesen Fehler  
  
1.  Initialisieren Sie den Klassenmember in einem regulären Konstruktor oder mit einer anderen Initialisierungsmethode.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1913 generiert:  
  
```  
// cs1912.cs class A { public delegate void D(); public event D myEvent; } public class Test { static void Main() { A a = new A() {myEvent = M}; // CS1913 } public void M(){} }  
```  
  
## Siehe auch  
 [Klassen und Strukturen](/dotnet/csharp/programming-guide/classes-and-structs/index)