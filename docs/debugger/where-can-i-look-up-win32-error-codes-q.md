---
title: Wo sind die Win32-Fehlercodes zu finden? | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecddd2a8ca87d4c86b3cdf776fcf2e475efb8836
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37056923"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Wo sind die Win32-Fehlercodes zu finden?
WINERROR.H im Verzeichnis INCLUDE der Standardsysteminstallation enthält die Definitionen der Fehlercodes für die Win32-API-Funktionen.  
  
 Sie können einen Fehlercode nachschlagen, den Code in die **Watch** Fenster oder die **Schnellüberwachung** im Dialogfeld. Zum Beispiel:  
  
`0x80000004,hr` 

  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von nativem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)