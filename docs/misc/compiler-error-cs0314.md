---
title: "Compilerfehler CS0314 | Microsoft Docs"
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
  - "CS0314"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0314"
ms.assetid: 12f68f51-0568-4e80-b0fd-15899807477d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0314
Der Typ "Typ1" kann nicht als Typparameter "Name" im generischen Typ oder in der generischen Methode "Name" verwendet werden. Es gibt keine Boxing\-Konvertierung oder Typparameterumwandlung von "Typ1" in "Typ2"".  
  
 Wenn ein generischer Typ einen Typparameter mit Einschränkungen verwendet, muss auch die neue Klasse diese Einschränkungen erfüllen.  
  
### So beheben Sie diesen Fehler  
  
1.  Fügen Sie im folgenden Beispiel `where T : ClassConstraint` der Klasse `B` hinzu.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0314 generiert:  
  
```  
// cs0314.cs // Compile with: /target:library public class ClassConstraint { } public class A<T> where T : ClassConstraint { } public class B<T> : A<T> //CS0314 { } // Try using this instead. public class C<T> : A<T> where T : ClassConstraint { }  
```  
  
## Siehe auch  
 [Einschränkungen für Typparameter](/dotnet/csharp/programming-guide/generics/constraints-on-type-parameters)