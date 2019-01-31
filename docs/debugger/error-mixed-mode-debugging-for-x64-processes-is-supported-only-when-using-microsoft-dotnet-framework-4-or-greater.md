---
title: 'Fehler: Im gemischten Modus Debuggen für X64 Prozesse wird nur unterstützt, wenn Microsoft .NET Framework, Version 4 oder höher | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 61c92460976ec9b95163b83744ee0b01b6ebc572
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54986084"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
Um gemischten systemeigenen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4. Das Debuggen von 64-Bit-Prozessen im gemischten Modus wird erst ab [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] 4 unterstützt.  
  
### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
- Führen Sie einen der folgenden Schritte aus:  
  
  - Aktualisieren Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] auf Version 4.  
  
  - Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.  
  
## <a name="see-also"></a>Siehe auch  
 [Remote Debugging](../debugger/remote-debugging.md)