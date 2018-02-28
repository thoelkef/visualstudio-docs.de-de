---
title: Wo sind die Win32-Fehlercodes zu finden? | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f48f3fbff8f7f18fa745df7ac9571c69038651e6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Wo sind die Win32-Fehlercodes zu finden?

          WINERROR.H im Verzeichnis INCLUDE der Standardsysteminstallation enthält die Definitionen der Fehlercodes für die Win32-API-Funktionen.  
  
 Sie können einen Fehlercode nachschlagen, dazu den Code in der **Überwachen** Fenster oder den **Schnellüberwachung** (Dialogfeld). Zum Beispiel:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von systemeigenem Code häufig gestellte Fragen](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)