---
title: "Compilerfehler CS0737 | Microsoft Docs"
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
  - "CS0737"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0737"
ms.assetid: d2247770-5546-46f2-a01d-8e2ebfcbb859
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0737
"Typname" implementiert den Schnittstellenmember "Membername" nicht. "Methodenname" ist nicht öffentlich und kann daher einen Schnittstellenmember nicht implementieren.  
  
 Eine Methode, die einen Schnittstellenmember implementiert, muss öffentlichen zugänglich sein. Alle Schnittstellenmember sind `public`.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie der Methode den [public](/dotnet/csharp/language-reference/keywords/public)\-Zugriffsmodifizierer hinzu.  
  
## Beispiel  
 Der folgende Code generiert CS0737:  
  
```  
// cs0737.cs interface ITest { // Default access of private with no modifier. int Return42(); // Try the following line instead. // public int Return42(); } struct Struct1 : ITest // CS0737 { int Return42() { return (42); } } public class Test { public static int Main(string[] args) { Struct1 s1 = new Struct1(); return (1); } }  
```  
  
## Siehe auch  
 [Schnittstellen](/dotnet/csharp/programming-guide/interfaces/index)