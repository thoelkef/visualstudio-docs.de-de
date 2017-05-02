---
title: "Konstanten, Enumerationen und Strukturen f&#252;r die Active Script-Profilerstellung | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6e079d84-9dde-46fc-8a6a-18e902f60ecc
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Konstanten, Enumerationen und Strukturen f&#252;r die Active Script-Profilerstellung
Die folgenden Enumerationen werden von Active Script\-Profilerschnittstellen verwendet.  
  
## Konstanten, Enumerationen und Strukturen  
  
|Konstanten|Beschreibung|  
|----------------|------------------|  
|[PROFILER\_EXTERNAL\_OBJECT\_ADDRESS\-Typ](../../winscript/reference/profiler-external-object-address-type.md)|Die externe Objektadresse des Profilers.  Wird verwendet in [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md) und [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Die ID des Heapobjekts.  Wird verwendet in [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md) [PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-scope-list-structure.md), [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) und [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md).|  
|[PROFILER\_HEAP\_OBJECT\_NAME\_ID\-Typ](../../winscript/reference/profiler-heap-object-name-id-type.md)|Die ID des Namens des Heapobjekts.  Wird in [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md) verwendet.|  
  
|Enumerationen|Beschreibung|  
|-------------------|------------------|  
|[PROFILER\_EVENT\_MASK\-Enumeration](../../winscript/reference/profiler-event-mask-enumeration.md)|Gibt die Typen von Ereignissen an, für die ein Profil erstellt werden soll.|  
|[PROFILER\_HEAP\_ENUM\_FLAGS\-Enumeration](../../winscript/reference/profiler-heap-enum-flags-enumeration.md)|Flags, die angeben, ob zusätzliche Informationen zu einem Heapobjekt, auf das in einer Objektbeziehung verwiesen wird, verfügbar gemacht werden.  Wird in der [IActiveScriptProfilerControl5::EnumHeap2\-Methode](../../winscript/reference/iactivescriptprofilercontrol5-enumheap2-method.md) verwendet.|  
|[PROFILER\_HEAP\_OBJECT\_FLAGS\-Enumeration](../../winscript/reference/profiler-heap-object-flags-enumeration.md)|Flags, die grundlegende Informationen über das Heapobjekt darstellen.  Wird in der [PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md) verwendet.|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\_TYPE\-Enumeration](../../winscript/reference/profiler-heap-object-optional-info-type-enumeration.md)|Stellt verschiedene Typen von optionalen Informationen dar.  Wird in [PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md) verwendet.|  
|[PROFILER\_RELATIONSHIP\_INFO\-Enumeration](../../winscript/reference/profiler-relationship-info-enumeration.md)|Stellt Informationen über das Objekt in der Beziehung dar.  Wird in [PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md) verwendet.|  
|[PROFILER\_SCRIPT\_TYPE\-Enumeration](../../winscript/reference/profiler-script-type-enumeration.md)|Legt den Typ des Skripts fest.|  
  
|Strukturen|Beschreibung|  
|----------------|------------------|  
|[PROFILER\_HEAP\_OBJECT\-Struktur](../../winscript/reference/profiler-heap-object-structure.md)|Stellt die Heapobjekte dar, die von der [IActiveScriptProfilerControl3::EnumHeap\-Methode](../../winscript/reference/iactivescriptprofilercontrol3-enumheap-method.md) erfasst werden.|  
|[PROFILER\_HEAP\_OBJECT\_OPTIONAL\_INFO\-Struktur](../../winscript/reference/profiler-heap-object-optional-info-structure.md)|Stellt optionale Informationen über Heapobjekte dar.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\-Struktur](../../winscript/reference/profiler-heap-object-relationship-structure.md)|Stellt eine Beziehung eines Heapobjekts dar.|  
|[PROFILER\_HEAP\_OBJECT\_RELATIONSHIP\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-relationship-list-structure.md)|Stellt eine Liste von Beziehungen dar, die zu einem Heapobjekt gehören.|  
|[PROFILER\_HEAP\_OBJECT\_SCOPE\_LIST\-Struktur](../../winscript/reference/profiler-heap-object-scope-list-structure.md)|Diese Struktur ist nur Funktionsobjekten zugeordnet.  Die Bereichsliste stellt den Schließvorgang für die Funktion als Liste von Bereichen dar, wobei jeder Bereich ein Heapobjekt mit einer zugeordneten Eigenschaftenliste ist, die Variablen in jedem angegebenen Bereich darstellt.  In einigen Fällen sind die Namen von Objekten in diesem Bereich möglicherweise nicht verfügbar, nur ihre IDs.|  
  
## Siehe auch  
 [Active Script Profiler\-Schnittstelle](../../winscript/reference/active-script-profiler-interfaces.md)