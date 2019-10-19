---
title: Active Script Profiler-Konstanten, Enumerationen und Strukturen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a9409799c7da2ed3f4864dea0e7785635492220
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572692"
---
# <a name="active-script-profiler-constants-enumerations-and-structures"></a>Konstanten, Enumerationen und Strukturen für die Active Script-Profilerstellung
Die folgenden Enumerationen werden von Active Script-Profilerschnittstellen verwendet.  
  
## <a name="constants-enumerations-and-structures"></a>Konstanten, Enumerationen und Strukturen  
  
|Konstanten|Beschreibung|  
|---------------|-----------------|  
|[PROFILER_EXTERNAL_OBJECT_ADDRESS-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse des Profilers. Wird in der [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md) und PROFILER_HEAP_OBJECT_RELATIONSHIP- [Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)verwendet.|  
|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts. Wird in [der PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md)[PROFILER_HEAP_OBJECT_SCOPE_LIST](../../winscript/reference/profiler-heap-object-scope-list-structure.md)-Struktur, [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)und PROFILER_HEAP_OBJECT_RELATIONSHIP- [Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)verwendet.|  
|[PROFILER_HEAP_OBJECT_NAME_ID-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID des Namens des Heapobjekts. Wird in der [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md)verwendet.|  
  
|Enumerationen|Beschreibung|  
|------------------|-----------------|  
|[PROFILER_EVENT_MASK-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md)|Gibt die Typen von Ereignissen an, für die ein Profil erstellt werden soll.|  
|[PROFILER_HEAP_ENUM_FLAGS-Enumeration](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flags, die angeben, ob zusätzliche Informationen zu einem Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden. Wird in der [IActiveScriptProfilerControl5:: EnumHeap2-Methode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md)verwendet.|  
|[PROFILER_HEAP_OBJECT_FLAGS-Enumeration](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flags, die grundlegende Informationen über das Heapobjekt darstellen. Wird in der [PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md)verwendet.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO_TYPE-Enumeration](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Stellt verschiedene Typen von optionalen Informationen dar. Wird in der [PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)verwendet.|  
|[PROFILER_RELATIONSHIP_INFO-Enumeration](../../winscript/reference/profiler-relationship-info-enumeration.md)|Stellt Informationen über das Objekt in der Beziehung dar. Wird in der [PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)verwendet.|  
|[PROFILER_SCRIPT_TYPE-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md)|Legt den Typ des Skripts fest.|  
  
|Strukturen|Beschreibung|  
|----------------|-----------------|  
|[PROFILER_HEAP_OBJECT-Struktur](../../winscript/reference/profiler-heap-object-structure.md)|Stellt die Heap Objekte dar, die von der [IActiveScriptProfilerControl3:: enumheap-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md)erfasst werden.|  
|[PROFILER_HEAP_OBJECT_OPTIONAL_INFO-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Stellt optionale Informationen über Heapobjekte dar.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Stellt eine Beziehung eines Heapobjekts dar.|  
|[PROFILER_HEAP_OBJECT_RELATIONSHIP_LIST-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Stellt eine Liste von Beziehungen dar, die zu einem Heapobjekt gehören.|  
|[PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Diese Struktur ist nur Funktionsobjekten zugeordnet. Die Bereichsliste stellt den Schließvorgang für die Funktion als Liste von Bereichen dar, wobei jeder Bereich ein Heapobjekt mit einer zugeordneten Eigenschaftenliste ist, die Variablen in jedem angegebenen Bereich darstellt. In einigen Fällen sind die Namen von Objekten in diesem Bereich möglicherweise nicht verfügbar, nur ihre IDs.|  
|[PROFILER_PROPERTY_TYPE_SUBSTRING_INFO-Struktur](../../winscript/reference/profiler-property-type-substring-info-structure.md)|Stellt Informationen über den Typ der Teil Zeichenfolge dar.|  
  
## <a name="see-also"></a>Siehe auch  
 [Active Script-Profilerschnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)