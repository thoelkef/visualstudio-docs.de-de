---
title: "Compilerfehler CS0453 | Microsoft Docs"
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
  - "CS0453"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0453"
ms.assetid: a1bbd09e-6313-4bfd-84bf-bc15a8d214a6
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0453
Der 'Type Name'\-Typ darf keine NULL\-Werte zulassen, wenn er als 'Parameter Name'\-Parameter im generischen Typ oder in der generischen 'Generic Identifier'\-Methode verwendet werden soll.  
  
 Dieser Fehler tritt auf, wenn Sie ein Typargument, das kein Werttyp ist, beim Instanziieren eines generischen Typs bzw. einer generischen Methode verwenden, für den bzw. die die **value**\-Einschränkung festgelegt ist. Er kann auch auftreten, wenn Sie ein Werttypargument verwenden, das nicht auf Null festgelegt werden kann. Siehe die beiden letzten Codezeilen im folgenden Beispiel.  
  
## Beispiel  
 Der folgende Code generiert diese Warnung.  
  
```  
// CS0453.cs using System; public class HV<S> where S : struct { } public class H1 : HV<string> { }                   // CS0453 public class H2 : HV<H1> { }                       // CS0453 public class H3<S> : HV<S> where S : class { }     // CS0453 public class H4 : HV<int?> { }                     // CS0453 public class H5 : HV<Nullable<Nullable<int>>> { }  // CS0453  
```