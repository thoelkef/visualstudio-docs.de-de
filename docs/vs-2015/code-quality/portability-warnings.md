---
title: Portabilitäts Warnungen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 932474143b4770e81d8bfca14ab05a6538ae84a8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671165"
---
# <a name="portability-warnings"></a>Portabilitätswarnungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Portabilitäts Warnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.

## <a name="in-this-section"></a>In diesem Abschnitt

|Regel|Beschreibung|
|----------|-----------------|
|[CA1900: Werttypfelder sollten portabel sein.](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Diese Regel überprüft, ob Strukturen, die mithilfe eines expliziten Layoutattributs deklariert werden, ordnungsgemäß ausgerichtet werden, wenn Sie auf 64-Bit-Betriebssystemen an nicht verwalteten Code gemarshallt werden.|
|[CA1901: P/Aufruf Deklarationen sollten portabel sein.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert von P/aufrufen aus und überprüft, ob ihre Größe beim Mars Hallen an nicht verwalteten Code auf 32-Bit-und 64-Bit-Betriebssystemen korrekt ist.|
|[CA1903: Nur API aus Zielframework verwenden.](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|
