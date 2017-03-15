---
title: "Compilerfehler CS0717 | Microsoft Docs"
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
  - "CS0717"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0717"
ms.assetid: 1976e82a-d048-4f13-a95a-a7f4e3cd7038
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0717
"Statische Klasse": Statische Klassen können nicht als Einschränkungen verwendet werden.  
  
 Statische Klassen können nicht erweitert werden, da sie nur statische Member und keine Instanzmember enthalten. Da sie nicht erweitert werden können, sind statische Klassen als Typparameter und Einschränkungen nutzlos, weil es keinen Typ geben kann, der eine Spezialisierung einer statischen Klasse ist.  
  
## Beispiel  
 Im folgenden Beispiel wird CS0717 generiert:  
  
```  
// CS0717.cs public static class SC { public static void F() { } } public class G<T> where T : SC  // CS0717 { public static void Main() { } }  
```