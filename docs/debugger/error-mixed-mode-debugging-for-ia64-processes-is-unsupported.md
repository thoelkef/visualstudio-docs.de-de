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
ms.openlocfilehash: f80cc0d38335679df413f104deadc8f9135ab765
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56715751"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Fehler: Debuggen im gemischten Modus wird für IA64-Prozesse nicht unterstützt
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger unterstützt das Debuggen von gemischtem systemeigenem und verwaltetem Code in Itanium-basierten Prozessen nicht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

-   Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)