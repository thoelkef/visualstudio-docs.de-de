---
title: "Compilerfehler CS1638 | Microsoft Docs"
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
  - "CS1638"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1638"
ms.assetid: 5279c060-5be3-4c29-80cc-21326d4cffdb
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1638
"Bezeichner" ist ein reservierter Bezeichner und kann nicht im ISO\-Sprachversionsmodus verwendet werden.  
  
 Wird durch den **\/langversion**\-Compilerschalter die Option für ISO\-Sprachkompatibilität angegeben, führt jeder Bezeichner, der irgendwo doppelte Unterstriche enthält, zu diesem Fehler. Um diesen Fehler zu vermeiden, entfernen Sie alle Bezeichner mit doppelten Unterstrichen, oder verzichten Sie darauf, die Option für die ISO\-1\-Sprachversion zu verwenden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1638 generiert:  
  
```  
// CS1638.cs // compile with: /langversion:ISO-1 class bad__identifer // CS1638 (double underscores are not ISO compliant) { } // Try this instead: //class GoodIdentifier //{ //} class CMain { public static void Main() { } }  
```  
  
## Siehe auch  
 [\/langversion \(Conformant Syntax\)](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option)