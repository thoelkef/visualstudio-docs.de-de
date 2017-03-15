---
title: "Compilerfehler CS0738 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0738"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0738"
ms.assetid: 01ce94ee-2435-4326-befc-2b020c441a4f
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0738
"Typname" implementiert den Schnittstellenmember "Membername" nicht. "Methodenname" kann "Schnittstellenmember" nicht implementieren, da er nicht den entsprechenden Rückgabetyp "Typname" hat.  
  
 Der Rückgabewert einer implementierenden Methode in einer Klasse muss dem Rückgabewert des Schnittstellenmembers entsprechen, den sie implementiert.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie den Rückgabetyp der Methode, damit er dem des Schnittstellenmembers entspricht.  
  
## Beispiel  
 Der folgende Code generiert CS0738, da die Klassenmethode `void` und der Schnittstellenmember mit dem gleichen Namen `int` zurückgibt:  
  
```  
using System; interface ITest { int TestMethod(); } public class Test: ITest { public void TestMethod() { } // CS0738 // Try the following line instead. // public int TestMethod(); }  
```  
  
## Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)