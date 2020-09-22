---
title: 'Vorgehensweise: Bearbeiten eines Registerwerts | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f0cd04b054d51119f6f6c1b0275c4f781656bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841105"
---
# <a name="how-to-edit-a-register-value"></a>Gewusst wie: Bearbeiten eines Registerwerts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Fenster „Register“ ist nur verfügbar, wenn Debuggen auf Adressebene im Dialogfeld **Optionen** im Knoten **Debuggen** aktiviert ist.  
  
### <a name="to-change-the-value-of-a-register"></a>So ändern Sie den Wert eines Registers  
  
1. Verschieben Sie die Einfügemarke im Fenster **Register** mithilfe der TAB-TASTE oder der Maus auf den zu ändernden Wert. Wenn Sie mit der Eingabe beginnen, muss sich der Cursor vor dem Wert befinden, der überschrieben werden soll.  
  
2. Geben Sie den neuen Wert ein.  
  
    > [!CAUTION]
    > Das Ändern von Registerwerten (insbesondere im EIP-Register und im EBP-Register) kann sich auf die Ausführung des Programms auswirken.  
  
    > [!CAUTION]
    > Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar unwesentliche Bearbeitung kann Änderungen in einigen Bits mit dem niedrigsten Wert in einem Gleitkommaregister bewirken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [How to: Verwenden des Fensters „Register“](../debugger/how-to-use-the-registers-window.md)
