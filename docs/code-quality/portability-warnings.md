---
title: Portabilitätswarnungen
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f48cef7ffaf08fc26566fdd04bee15a3e3e1b85f
ms.sourcegitcommit: 1efb6b219ade7c35068b79fbdc573a8771ac608d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/28/2020
ms.locfileid: "78167572"
---
# <a name="portability-warnings"></a>Portabilitätswarnungen
Portabilitäts Warnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|BESCHREIBUNG|
|----------|-----------------|
|[CA1900: Werttypfelder sollten portabel sein](../code-quality/ca1900.md)|Diese Regel überprüft, ob Strukturen, die mithilfe eines expliziten Layoutattributs deklariert werden, ordnungsgemäß ausgerichtet werden, wenn Sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden.|
|[CA1901: Deklarationen von P-Invoke müssen portabel sein](../code-quality/ca1901.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert von P/aufrufen aus und überprüft, ob ihre Größe beim Mars Hallen an nicht verwalteten Code auf 32-Bit-und 64-Bit-Betriebssystemen korrekt ist.|
|[CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|
