---
title: 'Vorgehensweise: Bearbeiten eines Registerwerts | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a84cd75dd6ae6ecd2e62bd41ed384cd03305bbf0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53963449"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Vorgehensweise: Bearbeiten eines Registerwerts (C#, C++, Visual Basic F#)

Das Fenster „Register“ ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.  
  
### <a name="to-change-the-value-of-a-register"></a>So ändern Sie den Wert eines Registers  
  
1.  Verschieben Sie die Einfügemarke im Fenster **Register** mithilfe der TAB-TASTE oder der Maus auf den zu ändernden Wert. Wenn Sie mit der Eingabe beginnen, muss sich der Cursor vor dem Wert befinden, der überschrieben werden soll.  
  
2.  Geben Sie den neuen Wert ein.  
  
    > [!CAUTION]
    >  Das Ändern von Registerwerten (insbesondere im EIP-Register und im EBP-Register) kann sich auf die Ausführung des Programms auswirken.  
  
    > [!CAUTION]
    >  Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar unwesentliche Bearbeitung kann Änderungen in einigen Bits mit dem niedrigsten Wert in einem Gleitkommaregister bewirken.  
  
## <a name="see-also"></a>Siehe auch  
 [Vorgehensweise: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)