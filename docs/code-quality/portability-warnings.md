---
title: Portability Warnings
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: jillre
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61efbc2022b2c0cd60e005936e148bbaf1d900a4
ms.sourcegitcommit: 00ba14d9c20224319a5e93dfc1e0d48d643a5fcd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2020
ms.locfileid: "77091729"
---
# <a name="portability-warnings"></a>Portability Warnings
Portabilitäts Warnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|BESCHREIBUNG|
|----------|-----------------|
|[CA1900: Werttypfelder sollten portabel sein](../code-quality/ca1900.md)|Diese Regel überprüft, ob Strukturen, die mithilfe eines expliziten Layoutattributs deklariert werden, ordnungsgemäß ausgerichtet werden, wenn Sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden.|
|[CA1901: Deklarationen von P-Invoke müssen portabel sein](../code-quality/ca1901.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert von P/aufrufen aus und überprüft, ob ihre Größe beim Mars Hallen an nicht verwalteten Code auf 32-Bit-und 64-Bit-Betriebssystemen korrekt ist.|
|[CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|
