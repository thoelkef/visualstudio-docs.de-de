---
title: "Compilerfehler CS0450 | Microsoft Docs"
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
  - "CS0450"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0450"
ms.assetid: 8eb0e98b-d7a1-49a7-8e55-36e2eb0057ff
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0450
'Type Parameter Name': Eine Einschränkungsklasse kann nicht gleichzeitig mit der Einschränkung 'class' oder 'struct' angegeben werden.  
  
 Wenn ein Typparameter durch eine Einschränkung des Typs 'struct' eingeschränkt wird, ist es logisch widersprüchlich, dass er auch durch einen bestimmten Klassentyp eingeschränkt wird, weil 'struct' und 'class' Kategorien darstellen, die sich gegenseitig ausschließen. Wenn ein Typparameter durch eine bestimmte Klassentypeinschränkung eingeschränkt ist, dann ist er gemäß Definition durch die Klassentypeinschränkung eingeschränkt. Die Angabe der Klassentypeinschränkung ist daher redundant.  
  
## Beispiel  
  
```  
// CS0450.cs // compile with: /t:library public class GenericsErrors { public class B { } public class G3<T> where T : struct, B { } // CS0450 // To resolve, use the following line instead: // public class G3<T> where T : B { } }  
```