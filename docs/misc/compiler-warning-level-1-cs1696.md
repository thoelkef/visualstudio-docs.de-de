---
title: "Compilerwarnung (Stufe 1) CS1696 | Microsoft Docs"
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
  - "CS1696"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1696"
ms.assetid: 69a45988-1aba-4a01-a84e-7ca59f8dde28
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1696
Einzeiliger Kommentar oder Zeilenende erwartet.  
  
 Der Compiler erfordert, dass auf eine Präprozessordirektive ein Zeilenabschlusszeichen oder ein einzeiliger Kommentar folgt. Der Compiler hat die Verarbeitung einer gültigen Präprozessordirektive abgeschlossen und etwas gefunden, das diese Syntaxeinschränkung verletzt.  
  
## Beispiel  
 Im folgenden Beispiel wird CS1696 generiert.  
  
```  
// CS1696.cs class Test { public static void Main() { #pragma warning disable 1030;219   // CS1696 #pragma warning disable 1030   // OK } }  
```