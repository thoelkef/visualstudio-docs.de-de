---
title: Portabilitätswarnungen
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6fe3bcd703d7fd58d5590b755a553d8ead4c0a9
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="portability-warnings"></a>Portabilitätswarnungen
Portabilitätswarnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1900: Werttypfelder sollten portabel sein](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Diese Regel überprüft, dass mithilfe eines Attributs explizitem Layout deklarierten Strukturen korrekt, beim Marshallen an nicht verwalteten Code auf 64-Bit-Betriebssystemen ausgerichtet werden.|
|[CA1901: Deklarationen von P/Invoke müssen portabel sein.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P/Invoke und stellt sicher, dass ihre Größe beim Marshallen an nicht verwalteten Code unter 32-Bit und 64-Bit-Betriebssystemen richtig ist.|
|[CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|