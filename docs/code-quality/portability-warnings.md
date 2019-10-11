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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 072858a9faafe312fd7c8314e7f25cf581c40844
ms.sourcegitcommit: e95dd8cedcd180e0bce6a75c86cf861757918290
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/09/2019
ms.locfileid: "72163070"
---
# <a name="portability-warnings"></a>Portabilitätswarnungen
Portabilitäts Warnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1900: Werttyp Felder sollten portabel sein @ no__t-0|Diese Regel überprüft, ob Strukturen, die mithilfe eines expliziten Layoutattributs deklariert werden, ordnungsgemäß ausgerichtet werden, wenn Sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden.|
|[CA1901: P/Aufruf Deklarationen sollten portabel sein @ no__t-0|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert von P/aufrufen aus und überprüft, ob ihre Größe beim Mars Hallen an nicht verwalteten Code auf 32-Bit-und 64-Bit-Betriebssystemen korrekt ist.|
|[CA1903: Verwenden Sie nur die API aus dem Ziel Framework @ no__t-0|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|
