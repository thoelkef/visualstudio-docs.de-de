---
title: "Alias definition is recursive. | Microsoft Docs"
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
  - "vs.message.0x800A00DA"
  - "vs.message.VS_E_RECURSIVEALIAS"
ms.assetid: e48a2908-9b94-4c6a-9807-beeeba71531c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Alias definition is recursive.
Im Allgemeinen tritt dieser Fehler auf, wenn ein Alias definiert wurde, der indirekt oder direkt auf sich selbst verweist.  
  
### So beheben Sie diesen Fehler  
  
1.  Ändern Sie die Aliasdefinition, und versuchen Sie es erneut.  
  
     – oder –  
  
2.  Überprüfen Sie die aktuelle Liste der Aliase und ihrer Definitionen, indem Sie im Befehlsfenster `>alias` eingeben, und versuchen Sie es erneut.  
  
## Siehe auch  
 [Befehl "Alias"](../ide/reference/alias-command.md)   
 [Visual Studio\-Befehlsaliase](../ide/reference/visual-studio-command-aliases.md)