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
ms.openlocfilehash: 0bddbb1572bd0258eae2052eb34dfa3d0d67a134
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737624"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Fehler: Debuggen im gemischten Modus wird für IA64-Prozesse nicht unterstützt
Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Debugger unterstützt das Debuggen von gemischtem systemeigenem und verwaltetem Code in Itanium-basierten Prozessen nicht.

### <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler

- Erstellen Sie eine 32-Bit-Version der Anwendung zum Debuggen.

## <a name="see-also"></a>Siehe auch
- [Remote Debugging](../debugger/remote-debugging.md)