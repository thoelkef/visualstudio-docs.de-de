---
title: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e8cfc3ac5cb606637fe5c2818750168a239a46fa
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852614"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
Um gemischten nativen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, benötigen Sie .NET Framework Version 4. Das Debuggen von 64-Bit-Prozessen im gemischten Modus mit .NET Framework wird erst ab Version 4 unterstützt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Führen Sie einen der folgenden Schritte aus:

  - Aktualisieren Sie .NET Framework auf Version 4.

  - Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)