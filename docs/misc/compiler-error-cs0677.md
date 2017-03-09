---
title: "Compilerfehler CS0677 | Microsoft Docs"
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
  - "CS0677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0677"
ms.assetid: 6a4a3703-9b44-4c4f-a564-8b437b1cb6b8
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0677
"Variable": Ein flüchtiges Feld kann nicht vom Typ "Typ" sein.  
  
 Mit dem `volatile`\-Schlüsselwort deklarierte Felder müssen einen der folgenden Typen aufweisen:  
  
-   Verweistyp  
  
-   Zeigertyp \(in einem `unsafe`\-Kontext\)  
  
-   die Typen `sbyte`, **byte**, **short**, `ushort`, `int`, `uint`, `char`, **float**, `bool`  
  
-   Enum\-Typen auf Grundlage der oben genannten Typen  
  
 Im folgenden Beispiel wird CS0677 generiert:  
  
```  
// CS0677.cs class TestClass { private volatile long i;   // CS0677 public static void Main() { } }  
```