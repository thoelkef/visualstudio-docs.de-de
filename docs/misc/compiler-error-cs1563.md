---
title: "Compilerfehler CS1563 | Microsoft Docs"
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
  - "CS1563"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1563"
ms.assetid: 67f84cd5-9209-43d6-b642-3628ef84ce4c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1563
Die Ausgabe "Ausgabedatei" hat keine Quelldateien.  
  
 Die Compileroption [\/out](/dotnet/csharp/language-reference/compiler-options/out-compiler-option) wurde angegeben, ohne dass danach Quellcodedateien folgen. Sie sollten **\/out** entweder nicht verwenden oder nach **\/out** die Quellcodedateien angeben.