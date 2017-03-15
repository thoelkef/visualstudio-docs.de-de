---
title: "Compilerwarnung (Stufe 1) CS3013 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS3013"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS3013"
ms.assetid: 00b3bbe1-f2a0-465c-be0e-1af700c5753d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerwarnung (Stufe 1) CS3013
Hinzugefügte Module müssen mit dem CLSCompliant\-Attribut markiert werden, damit sie mit der Assembly übereinstimmen.  
  
 Ein mit der Compileroption [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) kompiliertes Modul wurde einer Kompilierung mit [\/addmodule](/dotnet/csharp/language-reference/compiler-options/addmodule-compiler-option) hinzugefügt. Die Kompatibilität des Moduls mit der Common Language Specification \(CLS\) stimmt jedoch nicht mit dem CLS\-Zustand der aktuellen Kompilierung überein.  
  
 Die CLS\-Kompatibilität wird durch das Modulattribut angegeben.`[module:CLSCompliant(true)]` gibt z. B. an, dass das Modul CLS\-kompatibel ist, und `[module:CLSCompliant(false)]` gibt an, dass das Modul nicht CLS\-kompatibel ist. Die Standardeinstellung ist `[module:CLSCompliant(false)]`. Weitere Informationen zur CLS finden Sie unter [Sprachenunabhängigkeit und sprachunabhängige Komponenten](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md).