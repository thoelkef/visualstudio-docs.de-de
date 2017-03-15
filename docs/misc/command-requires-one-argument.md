---
title: "Command requires one argument. | Microsoft Docs"
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
  - "vs.message.VS_E_INCORRECTPARAMCOUNT1"
  - "vs.message.0x800A00C3"
ms.assetid: b4d98e6d-6970-42fb-b1de-43f2e952fb9d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Command requires one argument.
Im Allgemeinen tritt dieser Fehler auf, wenn keine ausreichenden Informationen für den Befehl eingegeben wurden oder eine falsche Kombination von Argumenten verwendet wurde.  
  
 Wenn z. B. `alias` `/delete sample1 sample2` für den `alias`\-Befehl eingegeben wurde, wird dieser Fehler angezeigt, weil Alias `/delete` nur einen einzigen Aliasnamen annehmen kann.  Aliasnamen enthalten keine Leerzeichen, deshalb wird `sample1 sample2` vom Feld Suchen und vom Befehlsfenster als zwei verschiedene Aliasnamen interpretiert.  
  
### So beheben Sie diesen Fehler  
  
1.  Schlagen Sie die korrekte Befehlssyntax in der Dokumentation nach, und versuchen Sie es erneut.  
  
## Siehe auch  
 [Visual Studio\-Befehle](../ide/reference/visual-studio-commands.md)