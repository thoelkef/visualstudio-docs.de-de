---
title: "Compilerfehler Error CS0425 | Microsoft Docs"
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
  - "CS0425"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0425"
ms.assetid: cec0391c-a641-43bc-8557-92b23f6ca685
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler Error CS0425
Die Einschränkungen für den Typparameter "Typparameter" der "Methode"\-Methode müssen mit den Einschränkungen für den Typparameter "Typparameter" der "Methode"\-Schnittstellenmethode übereinstimmen. Erwägen Sie stattdessen eine explizite Schnittstellenimplementierung.  
  
 Dieser Fehler tritt auf, wenn eine virtuelle generische Methode in einer abgeleiteten Klasse überschrieben wird und die Einschränkungen für die Methode in der abgeleiteten Klasse nicht mit den Einschränkungen für die Methode in der Basisklasse übereinstimmen. Um diesen Fehler zu vermeiden, stellen Sie sicher, dass die `where`\-Klausel in beiden Deklarationen identisch ist, oder nehmen Sie eine explizite Schnittstellenimplementierung vor.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS0425 generiert:  
  
```  
// CS0425.cs class C1 { } class C2 { } interface IBase { void F<ItemType>(ItemType item) where ItemType : C1; } class Derived : IBase { public void F<ItemType>(ItemType item) where ItemType : C2  // CS0425 { } } class CMain { public static void Main() { } }  
```  
  
## Beispiel  
 Die Einschränkungen brauchen keine wortwörtliche Entsprechung zu sein, solange sie dieselbe Bedeutung haben. Folgender Code beispielsweise ist zulässig:  
  
```  
// CS0425b.cs interface J<Z> { } interface I<S> { void F<T>(S s, T t) where T: J<S>, J<int>; } class C : I<int> { public void F<X>(int s, X x) where X : J<int> { } public static void Main() { } }  
```