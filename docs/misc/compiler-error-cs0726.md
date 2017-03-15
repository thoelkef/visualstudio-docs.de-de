---
title: "Compilerfehler CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS0726
"format specifier" ist kein gültiger Formatbezeichner  
  
 Dieser Fehler tritt im Debugger auf. Wenn Sie einen Variablennamen in einem der Debugfenster eingeben, können Sie diesem ein Komma und dann einen Formatbezeichner anfügen. Beispiele: `myInt, h` und `myString,nq`. Dieser Fehler tritt auf, wenn der Compiler den [Formatbezeichner in C\#](../debugger/format-specifiers-in-csharp.md) nicht erkennt.