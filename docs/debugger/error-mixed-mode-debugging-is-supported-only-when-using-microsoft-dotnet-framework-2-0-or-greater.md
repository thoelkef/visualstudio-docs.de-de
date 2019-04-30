---
title: 'Fehler: Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder höher unterstützt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_to_old
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
ms.openlocfilehash: 2fb4d0dfaeb944700757c9ceec222dbd62dab9dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850678"
---
# <a name="error-mixed-mode-debugging-is-supported-only-when-using-microsoft-net-framework-20-or-greater"></a>Fehler: Debuggen im gemischten Modus wird nur bei Verwendung von Microsoft .NET Framework, Version 2.0 oder höher, unterstützt
Um gemischten systemeigenen und verwalteten Code zu debuggen, müssen Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], Version 2.0, 3.0, 3.5 oder 4 verwenden. Das Debuggen im gemischten Modus mit früheren Versionen von [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] wird nicht unterstützt.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Aktualisieren Sie [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] auf Version 2.0, 3.0, 3.5 oder 4.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)