---
title: "Portabilit&#228;tswarnungen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.PortabilityRules"
helpviewer_keywords: 
  - "Portabilitätswarnungen"
  - "Analysen für verwalteten Code (Warnungen), Portabilitätswarnungen"
  - "Warnungen, Portabilität"
ms.assetid: 902e859a-2153-4970-baaa-8a5b4a11806f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# Portabilit&#228;tswarnungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Portabilitätswarnungen unterstützen die Portabilität über verschiedene Betriebssysteme hinweg.  
  
## In diesem Abschnitt  
  
|Regel|**Beschreibung**|  
|-----------|----------------------|  
|[CA1900: Werttypfelder sollten portabel sein](../code-quality/ca1900-value-type-fields-should-be-portable.md)|Anhand dieser Regel wird überprüft, ob die mit einem explizitem Layoutattribut deklarierten Strukturen korrekt ausgerichtet werden, wenn sie auf 64\-Bit\-Betriebssystemen an nicht verwalteten Code gemarshallt werden.|  
|[CA1901: Deklarationen von P\/Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P\/Invoke\-Deklaration aus und überprüft die zugehörige Größe beim Marshallen an nicht verwalteten Code unter einem 32\-Bit\- oder 64\-Bit\-Betriebssystem.|  
|[CA1903: Nur API aus Zielframework verwenden](../code-quality/ca1903-use-only-api-from-targeted-framework.md)|Ein Member oder Typ verwendet ein Member oder einen Typ, das bzw. der in einem Service Pack eingeführt wurde, das nicht im Zielframework des Projekts enthalten ist.|