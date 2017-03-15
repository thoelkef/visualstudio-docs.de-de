---
title: "Compilerwarnung (Stufe 1) CS1720 | Microsoft Docs"
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
  - "CS1720"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1720"
ms.assetid: 97adc294-3a4c-4418-a4ed-ccff43125b62
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1720
Der Ausdruck führt immer zu System.NullReferenceException, da der Standardwert von "generischer Typ" NULL ist.  
  
 Der Fehler tritt auf, wenn Sie einen Ausdruck schreiben, der den Standardwert einer Variablen des generischen Typs enthält, die ein Verweistyp \(z. B. eine Klasse\) ist. Betrachten Sie hierzu den folgenden Ausdruck:  
  
```  
default(T).ToString()  
```  
  
 Da `T` ein Verweistyp ist, lautet der Standardwert NULL. Beim Versuch, die <xref:System.Object.ToString%2A>\-Methode anzuwenden, wird deshalb eine <xref:System.NullReferenceException> ausgelöst.  
  
## Beispiel  
 Durch die Klassenverweiseinschränkung für Typ `T` wird sichergestellt, dass `T` ein Verweistyp ist.  
  
 Im folgenden Beispiel wird CS1720 generiert.  
  
```  
// CS1720.cs using System; public class Tester { public static void GenericClass<T>(T t1) where T : class { Console.WriteLine(default(T).ToString());  // CS1720 } public static void Main() {} }  
```