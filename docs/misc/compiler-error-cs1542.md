---
title: "Compilerfehler CS1542 | Microsoft Docs"
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
  - "CS1542"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1542"
ms.assetid: d7f60aa2-6645-472c-ac12-fa57a09fbd87
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1542
„dll“ kann nicht zu dieser Assembly hinzugefügt werden, da es sich bereits um eine Assembly handelt. Verwenden Sie stattdessen die Option \/R.  
  
 Die Datei, auf die mit der Compileroption [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) verwiesen wurde, wurde nicht mit [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) erstellt. Verwenden Sie [\/reference](/dotnet/csharp/language-reference/compiler-options/reference-compiler-option), um auf die Datei in dieser Kompilierung zu verweisen.