---
title: Wo sind die Win32-Fehlercodes zu finden? | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.errors
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- error codes, Win32
- Win32, error codes
ms.assetid: 8fb4ff42-b8eb-4152-b49e-b802d194b05e
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d403315a2320589f69174109d55c8726ffd5f673
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58958573"
---
# <a name="where-can-i-look-up-win32-error-codes"></a>Wo sind die Win32-Fehlercodes zu finden?
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WINERROR.H im Verzeichnis INCLUDE der Standardsysteminstallation enthält die Definitionen der Fehlercodes für die Win32-API-Funktionen.  
  
 Sie können den Fehlercode nachsehen, indem Sie den Code im **Überwachungsfenster** oder im Dialogfeld **Schnellüberwachung** eingeben. Zum Beispiel:  
  
```  
0x80000004,hr  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Debugging Native Code FAQs (Häufig gestellte Fragen zum Debuggen von nativem Code)](../debugger/debugging-native-code-faqs.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)
