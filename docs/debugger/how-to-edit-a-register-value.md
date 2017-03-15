---
title: "Gewusst wie: Bearbeiten eines Registerwerts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.register.edit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Registerwerte"
  - "Register (Fenster), Bearbeiten von Registerwerten"
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Gewusst wie: Bearbeiten eines Registerwerts
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Fenster Register ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.  
  
### So ändern Sie den Wert eines Registers  
  
1.  Verschieben Sie die Einfügemarke im Fenster **Register** mithilfe der TAB\-TASTE oder der Maus auf den zu ändernden Wert.  Wenn Sie mit der Eingabe beginnen, muss sich der Cursor vor dem Wert befinden, der überschrieben werden soll.  
  
2.  Geben Sie den neuen Wert ein.  
  
    > [!CAUTION]
    >  Das Ändern von Registerwerten \(insbesondere im EIP\-Register und im EBP\-Register\) kann sich auf die Ausführung des Programms auswirken.  
  
    > [!CAUTION]
    >  Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal\-zu\-Binär\-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen.  Auch eine scheinbar unwesentliche Bearbeitung kann Änderungen in einigen Bits mit dem niedrigsten Wert in einem Gleitkommaregister bewirken.  
  
## Siehe auch  
 [Gewusst wie: Verwenden des Fensters "Register"](../debugger/how-to-use-the-registers-window.md)