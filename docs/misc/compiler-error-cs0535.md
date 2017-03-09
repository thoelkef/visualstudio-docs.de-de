---
title: "Compilerfehler CS0535 | Microsoft Docs"
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
  - "CS0535"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0535"
ms.assetid: 282ed5d6-acb7-445b-999f-27a973ccc0b5
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0535
'Klasse' implementiert den Schnittstellenmember 'Member' nicht.  
  
 Eine [Klasse](/dotnet/csharp/language-reference/keywords/class), die von einer [Schnittstelle](/dotnet/csharp/language-reference/keywords/interface) abgeleitet wird, aber die Klasse hat mindestens ein Member der Schnittstelle nicht implementiert. Eine Klasse muss alle Member der Schnittstellen implementieren, von denen sie abgeleitet wird, oder ansonsten als `abstract` deklariert werden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0535 generiert:  
  
```  
// CS0535.cs public interface A { void F(); } public class B : A {}   // CS0535 A::F is not implemented // OK public class C : A { public void F() {} public static void Main() {} }  
```  
  
## Beispiel  
 Im folgenden Beispiel wird CS0535 generiert:  
  
```  
// CS0535_b.cs using System; class C : IDisposable {}   // CS0535 // OK class D : IDisposable { void IDisposable.Dispose() {} public void Dispose() {} static void Main() { using (D d = new D()) {} } }  
```