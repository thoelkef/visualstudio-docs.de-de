---
title: "Character set is missing &#39;]&#39;. | Microsoft Docs"
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
  - "vs.message.VS_E_RE_SETMISSINGCLOSE"
  - "vs.message.0x800A00C0"
ms.assetid: 97d2436c-498d-4eb0-a08c-8efcc7797fc0
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Character set is missing &#39;]&#39;.
Im Allgemeinen tritt dieser Fehler auf, wenn die schließende Klammer \(`]`\) für einen angegebenen regulären Ausdruck in einer Such\- oder Ersetzungszeichenfolge fehlt.  
  
### So beheben Sie diesen Fehler  
  
1.  Suchen Sie das Literalzeichen `]` mit `\]`.  
  
2.  Zum Suchen einer Zeichenliste geben Sie die fehlende Klammer `]` ein.  
  
## Siehe auch  
 [Verwenden von regulären Ausdrücken in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)   
 [NIB: Find and Replace, Quick Find](http://msdn.microsoft.com/de-de/dad03582-4931-4893-83ba-84b37f5b1600)   
 [Suchen in Dateien](../ide/find-in-files.md)