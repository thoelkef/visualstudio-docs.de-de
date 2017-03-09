---
title: "Compilerfehler CS0312 | Microsoft Docs"
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
  - "CS0312"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0312"
ms.assetid: 552db0ae-2ecf-4beb-9606-bbe58e5708f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0312
Der Typ "Typ1" kann nicht als Typparameter "Name" im generischen Typ oder in der generischen Methode "Name" verwendet werden. Der Typ "Typ1", der NULL\-Werte zulässt, entspricht nicht der Einschränkung von "Typ2".  
  
 Ein Typ, der NULL\-Werte zulässt, unterscheidet sich seinem Gegenstück, das keine NULL\-Werte zulässt. Es gibt keine implizite Verweiskonvertierung oder Identifizierungskonvertierung zwischen diesen beiden. Eine Boxing\-Konvertierung, die NULL\-Werte zulässt, erfüllt keine generische Typeinschränkung. Im folgenden Beispiel ist der erste Typparameter ein `Nullable<int>` und der zweite Typparameter ein `System.Int32`.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie die Einschränkung.  
  
2.  Im folgenden Beispiel müssen Sie das zweite Typargument entweder mit `int?` oder mit `object` deklarieren.  
  
## Beispiel  
 Mit dem folgenden Code wird CS0312 generiert:  
  
```  
// cs0312.cs class Program { static void MTyVar<T, U>() where T : U { } static int Main() { MTyVar<int?, int>(); // CS0312 return 1; } }  
```  
  
 Obwohl sich ein Typ, der NULL\-Werte zulässt, von einem Typ unterscheidet, der keine NULL\-Werte zulässt, sind verschiedene Arten von Konvertierung zwischen Werten, die NULL\-Werte zulassen, und Werten zulässig, die keine NULL\-Werte zulassen.  
  
## Siehe auch  
 [Typen, die NULL\-Werte zulassen](/dotnet/csharp/programming-guide/nullable-types/index)