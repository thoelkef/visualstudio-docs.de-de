---
title: "Portabilitätswarnungen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.PortabilityRules
helpviewer_keywords:
- portability warnings
- managed code analysis warnings, portability warnings
- warnings, portability
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 112f3686f2a3d21b2d5d493498b42e9b63fdb05b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="portability-warnings"></a>Portabilitätswarnungen
Portabilitätswarnungen unterstützen die Portabilität auf verschiedenen Betriebssystemen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
  
|Regel|Beschreibung|  
|----------|-----------------|  
|[CA1900: Werttypfelder sollten portabel sein](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Diese Regel überprüft, dass mithilfe eines Attributs explizitem Layout deklarierten Strukturen korrekt, beim Marshallen an nicht verwalteten Code auf 64-Bit-Betriebssystemen ausgerichtet werden.|  
|[CA1901: Deklarationen von P/Invoke müssen portabel sein.](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P/Invoke und stellt sicher, dass ihre Größe beim Marshallen an nicht verwalteten Code unter 32-Bit und 64-Bit-Betriebssystemen richtig ist.|  
|[CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|