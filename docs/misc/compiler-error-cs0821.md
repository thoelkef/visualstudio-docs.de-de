---
title: "Compilerfehler CS0821 | Microsoft Docs"
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
  - "CS0821"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0821"
ms.assetid: ef449115-93e8-4fa5-848a-d30dc7f68ddf
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0821
Implizit typisierte lokale Variablen können nicht als 'fixed' deklariert werden.  
  
 Implizit typisierte lokale Variablen und anonyme Typen werden im `fixed`\-Kontext nicht unterstützt.  
  
### So beheben Sie diesen Fehler  
  
1.  Entfernen Sie den `fixed`\-Modifizierer aus der Variablen, oder weisen Sie der Variablen einen expliziten Typ zu.  
  
## Beispiel  
 Mit dem folgenden Code wird der Fehler CS0821 generiert:  
  
```  
class A { static int x; public static int Main() { unsafe { fixed (var p = &x) { } } return -1; } }  
```  
  
## Siehe auch  
 [Implizit typisierte lokale Variablen](/dotnet/csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables)