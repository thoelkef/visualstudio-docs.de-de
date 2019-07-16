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
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745438"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Fehler: Debuggen im gemischten Modus für x64-Prozess wird nur bei Verwendung von Microsoft .NET Framework, Version 4 oder höher, unterstützt
Um gemischten systemeigenen und verwalteten Code in einem 64-Bit-Prozess zu debuggen, müssen Sie .NET Framework, Version 4 verfügen. Debuggen im gemischten Modus von 64-Bit-Prozessen mit .NET Framework-Versionen vor 4 wird nicht unterstützt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Führen Sie einen der folgenden Schritte aus:

  - Aktualisieren Sie .NET Framework, Version 4.

  - Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)