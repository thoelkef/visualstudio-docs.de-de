---
title: "Compilerfehler CS1109 | Microsoft Docs"
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
  - "CS1109"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1109"
ms.assetid: bebe56b8-3831-4ebb-a49e-e0364b4c11a7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1109
Die Erweiterungsmethoden müssen in statischen Klassen auf oberster Ebene definiert werden. 'Name' ist eine geschachtelte Klasse.  
  
 Erweiterungsmethoden können nicht in geschachtelten Klassen definiert werden.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1109 generiert, da die `Extension`\-Klasse in der `Out`\-Klasse geschachtelt ist:  
  
```  
// cs1109.cs public class Test { } static class Out { static class Extension { static void ExtMethod(this Test c) // CS1109 { } } }  
```  
  
## Siehe auch  
 [Erweiterungsmethoden](/dotnet/csharp/programming-guide/classes-and-structs/extension-methods)