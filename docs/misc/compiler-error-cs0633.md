---
title: "Compilerfehler CS0633 | Microsoft Docs"
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
  - "CS0633"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0633"
ms.assetid: a24d310b-151a-45eb-b150-3407940ec24c
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0633
Das Argument für das Attribut "Attribut" muss ein gültiger Bezeichner sein.  
  
 Jedes Argument, das Sie den Attributen <xref:System.Diagnostics.ConditionalAttribute> oder <xref:System.Runtime.CompilerServices.IndexerNameAttribute> übergeben, muss ein gültiger Bezeichner sein. Es dürfen also keine Zeichen wie "\+" enthalten sein, die in Bezeichnern ungültig sind.  
  
## Beispiel  
 In diesem Beispiel wird der Fehler CS0633 bei Verwendung von <xref:System.Diagnostics.ConditionalAttribute> veranschaulicht. Im folgenden Beispiel wird CS0633 generiert.  
  
```  
// CS0633a.cs #define DEBUG using System.Diagnostics; public class Test { [Conditional("DEB+UG")]   // CS0633 // try the following line instead // [Conditional("DEBUG")] public static void Main() { } }  
```  
  
## Beispiel  
 In diesem Beispiel wird der Fehler CS0633 bei Verwendung von <xref:System.Runtime.CompilerServices.IndexerNameAttribute> veranschaulicht.  
  
```  
// CS0633b.cs // compile with: /target:module #define DEBUG using System.Runtime.CompilerServices; public class Test { [IndexerName("Invalid+Identifier")]   // CS0633 // try the following line instead // [IndexerName("DEBUG")] public int this[int i] { get { return i; } } }  
  
```