---
title: "Compilerfehler CS1008 | Microsoft Docs"
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
  - "CS1008"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1008"
ms.assetid: e595a431-2cf0-4cc1-998f-94aecb2a6db1
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1008
Typ "byte", "sbyte", "short", "ushort", "int", "uint", "long" oder "ulong" erwartet.  
  
 Bestimmte Datentypen, z. B. [Enumerationen](/dotnet/csharp/language-reference/keywords/enum), können nur zum Speichern von Daten mit angegebenen Typen deklariert werden.  
  
 Im folgenden Beispiel wird CS1008 generiert:  
  
```  
// CS1008.cs abstract public class clx { enum splitch : char   // CS1008, char not valid type for enums { x, y, z } public static void Main() { } }  
```