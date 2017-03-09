---
title: "Compilerfehler CS0739 | Microsoft Docs"
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
  - "CS0739"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0739"
ms.assetid: c2a83015-401c-4d85-bb19-ed29800904c1
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0739
'Typname' TypeForwardedToAttribute\-Duplikat.  
  
 Eine Assembly kann mehr als ein <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> für einen externen Typ aufweisen.  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen und entfernen Sie das doppelte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>.  
  
## Beispiel  
 Der folgende Code generiert CS0739:  
  
```  
// CS0739.cs // CS0739 // Assume that a class Test is declared in a separate dll // with a namespace that is named cs739dll. [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] [assembly: System.Runtime.CompilerServices.TypeForwardedTo(typeof(cs739dll.Test))] namespace cs0739 { class Program { static void Main(string[] args) { } } }  
```  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>