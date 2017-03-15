---
title: "Compilerwarnung (Stufe 3) CS0659 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0659"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0659"
ms.assetid: 63435ee6-c92f-4124-95d4-d8f4e5f0af80
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 3) CS0659
'Klasse' überschreibt Object.Equals\(object o\), aber nicht Object.GetHashCode\(\).  
  
 Der Compiler hat eine Überschreibung der **Equals**\-Funktion, aber keine Überschreibung für **GetHashCode** erkannt. Eine Überschreibung von **Equals** bedeutet, dass Sie auch **GetHashCode** überschreiben möchten.  
  
 Weitere Informationen finden Sie unter  
  
-   <xref:System.Collections.Hashtable>.  
  
-   [Gleichheitsoperatoren](../Topic/Equality%20Operators.md)  
  
-   [NIB: Implementieren der Equals\-Methode](http://msdn.microsoft.com/de-de/30f28aaf-8b9e-46cd-a746-58a12473af2c)  
  
-   <xref:System.Object.GetHashCode%2A>  
  
 Im folgenden Beispiel wird CS0659 generiert:  
  
```  
// CS0659.cs // compile with: /W:3 /target:library class Test { public override bool Equals(object o) { return true; }   // CS0659 } // OK class Test2 { public override bool Equals(object o) { return true; } public override int GetHashCode() { return 0; } }  
```