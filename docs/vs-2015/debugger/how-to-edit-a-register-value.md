---
title: 'Vorgehensweise: Bearbeiten eines Registerwerts | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 465ecd4e8003b82a0a7dfbab33004ef2b80d7f32
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515761"
---
# <a name="how-to-edit-a-register-value"></a>Gewusst wie: Bearbeiten eines Registerwerts
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Bearbeiten eines Registerwerts](https://docs.microsoft.com/visualstudio/debugger/how-to-edit-a-register-value).  
  
Das Fenster Register ist nur verfügbar, wenn Debuggen auf Adressebene im aktiviert ist die **Optionen** Dialogfeld **Debuggen** Knoten.  
  
### <a name="to-change-the-value-of-a-register"></a>So ändern Sie den Wert eines Registers  
  
1.  In der **registriert** Fenster verwenden, die TAB-Taste oder der Maus zum Verschieben der Einfügemarke zu den Wert, die Sie ändern möchten. Wenn Sie mit der Eingabe beginnen, muss sich der Cursor vor dem Wert befinden, der überschrieben werden soll.  
  
2.  Geben Sie den neuen Wert ein.  
  
    > [!CAUTION]
    >  Das Ändern von Registerwerten (insbesondere im EIP-Register und im EBP-Register) kann sich auf die Ausführung des Programms auswirken.  
  
    > [!CAUTION]
    >  Das Bearbeiten von Gleitkommawerten kann aufgrund der Dezimal-zu-Binär-Konvertierung von Nachkommastellen zu geringfügigen Ungenauigkeiten führen. Auch eine scheinbar unwesentliche Bearbeitung kann Änderungen in einigen Bits mit dem niedrigsten Wert in einem Gleitkommaregister bewirken.  
  
## <a name="see-also"></a>Siehe auch  
 [Gewusst wie: Verwenden des Fensters "Register"](../debugger/how-to-use-the-registers-window.md)





