---
title: "Compilerfehler CS1617 | Microsoft Docs"
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
  - "CS1617"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1617"
ms.assetid: fd3371ed-39eb-4d3d-b8f5-d96ac0c79398
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Compilerfehler CS1617
'Option' ist eine ungültige Option für \/langversion; gültig sind 'ISO\-1', 'ISO\-2' oder 'Default'.  
  
 Dieser Fehler tritt auf, wenn Sie den Befehlszeilenschalter oder die Projekteinstellung [\/langversion](/dotnet/csharp/language-reference/compiler-options/langversion-compiler-option) verwendet, aber keine gültige Sprachoption angegeben haben. Überprüfen Sie die Syntax der Befehlszeile oder die Projekteinstellung, und ändern Sie sie in eine der aufgeführten Optionen, um diesen Fehler zu beheben.  
  
 Beim Kompilieren mit `csc /langversion:ISO` wird z. B. der Fehler CS1617 generiert.