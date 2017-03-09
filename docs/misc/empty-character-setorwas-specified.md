---
title: "Leerer Zeichensatz wurde angegeben. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_EMPTYSET"
  - "vs.message.0x800A00DF"
ms.assetid: 27ed2ebe-a492-4bc9-ab33-a09fba6cf1d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Leerer Zeichensatz wurde angegeben.
Dieser Fehler tritt normalerweise auf, wenn die Option für reguläre Ausdrücke ausgewählt wurde und für die Muster **Zeichensatz \[\]** oder **Zeichen nicht im Zeichensatz \[^\]** eine Zeichenfolge mit unvollständiger Syntax angegeben wurde.  Beispielsweise `[}`.  
  
### So beheben Sie diesen Fehler  
  
1.  Überprüfen Sie die Syntaxinformationen zum regulären Ausdruck, und geben Sie die Zeichenfolge erneut ein.  
  
## Siehe auch  
 [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/de-de/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Suchen in Dateien](../ide/find-in-files.md)   
 [Suchen und Ersetzen von Text](../ide/finding-and-replacing-text.md)