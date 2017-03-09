---
title: "Compilerwarnung (Stufe 1) CS1692 | Microsoft Docs"
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
  - "CS1692"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1692"
ms.assetid: 1a6d52e1-0ebb-4990-ac0b-36b05a884a19
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS1692
Ungültige Zahl  
  
 Für eine Reihe von Präprozessordirektiven, etwa `#pragma` und `#line`, werden Zahlen als Parameter verwendet. Eine dieser Zahlen ist ungültig, da sie zu groß ist, das falsche Format hat, ungültige Zeichen enthält usw. Um diesen Fehler zu beheben, korrigieren Sie die Zahl.  
  
## Beispiel  
 Im folgenden Beispiel wird der Fehler CS1692 generiert:  
  
```  
// CS1692.cs #pragma warning disable a  // CS1692 // Try this instad: // #pragma warning disable 1691 class A { static void Main() { } }  
```