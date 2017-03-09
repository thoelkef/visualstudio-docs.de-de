---
title: "Compilerfehler CS1518 | Microsoft Docs"
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
  - "CS1518"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1518"
ms.assetid: 26e0870d-fe91-4c66-b3f8-ed2b074c964e
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1518
Klasse, Delegat, Enumeration, Schnittstelle oder Struktur erwartet.  
  
 Eine Deklaration wurde gefunden, die in einem [Namespace](/dotnet/csharp/language-reference/keywords/namespace) nicht unterstützt wird. Innerhalb eines Namespace nimmt der Compiler nur Klassen, Strukturen, Enumerationen, Schnittstellen, Namespaces und Delegaten an.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1518 generiert:  
  
```  
// CS1518.cs namespace x { sealed class c1 {};      // OK namespace f2 {};         // OK sealed f3 {};            // CS1518 }  
```