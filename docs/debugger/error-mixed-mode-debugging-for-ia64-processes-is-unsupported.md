---
title: 'Fehler: Debuggen im gemischten Modus für IA64-Prozesse wird nicht unterstützt | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c4414651249aa7622e7f7be59e6150a4925f1b8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62850863"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Fehler: Debuggen im gemischten Modus wird auf Windows 64-Bit-Plattformen nicht unterstützt
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger unterstützt das Debuggen von gemischtem systemeigenem und verwaltetem Code in Itanium-basierten Prozessen nicht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)