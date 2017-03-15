---
title: "Compilerfehler CS0123 | Microsoft Docs"
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
  - "CS0123"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0123"
ms.assetid: 57be2c58-6d87-40af-9376-cd7f91023044
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0123
Keine Überladung für 'methode' stimmt mit dem Delegat 'delegat' überein  
  
 Fehler bei dem Versuch, einen Delegaten zu erstellen, da nicht die richtige Signatur verwendet wurde. Instanzen eines Delegaten müssen mit der gleichen Signatur wie die Delegatdeklaration deklariert werden.  
  
 Sie können diesen Fehler beheben, indem Sie entweder die Methoden\- oder die Delegatsignatur anpassen. Weitere Informationen finden Sie unter [Delegaten](/dotnet/csharp/programming-guide/delegates/index).  
  
 Im folgenden Beispiel wird CS0123 generiert:  
  
```  
// CS0123.cs delegate void D(); delegate void D2(int i); public class C { public static void f(int i) {} public static void Main() { D d = new D(f);   // CS0123 D2 d2 = new D2(f);   // OK } }  
```