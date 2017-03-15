---
title: "Compilerfehler CS0819 | Microsoft Docs"
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
  - "CS0819"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0819"
ms.assetid: a5369e03-eb7d-4c88-b390-51304bd8d1ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0819
Implizit typisierte Locals dürfen nicht mehrere Deklaratoren haben.  
  
 In expliziten Typdeklarationen sind mehrere Deklaratoren, aber nicht mit implizit typisierten Variablen erlaubt.  
  
### So beheben Sie diesen Fehler  
  
1.  Sie sollten die Deklaration und Wertzuweisung jeder implizit typisierten lokalen Variablen in einer separaten Zeile vornehmen.  
  
## Beispiel  
 Durch den folgenden Code wird der Fehler CS0819 ausgelöst:  
  
```  
// cs0819.cs class A { public static int Main() { var a = 3, b = 2; // CS0819 return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)