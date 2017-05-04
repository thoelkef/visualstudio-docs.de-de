---
title: "PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur
Diese Struktur wird mit nur Funktionsobjekten zugeordnet.  Die Bereichsliste stellt den Abschluss für die Funktion als Liste von Bereichen dar, in der jeder Bereich ein Heapobjekt mit einer zugeordneten Eigenschaftenliste ist, die Variablen in den angegebenen Bereich darstellt.  In einigen Fällen können die Namen von Objekten in diesem Bereich nicht verfügbar, und nur ihr Index in der Eigenschaftenliste ist verfügbar.  
  
## Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST  
{  
    UINT count;  
    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];  
} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
  
```  
  
## Mitglieder  
  
|Member|Text \[Type\]|Description|  
|------------|-------------------|-----------------|  
|count|UINT|Die Anzahl von Bereichen|  
|scopes|[PROFILER\_HEAP\_OBJECT\_ID\-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Ein Array Bereiche.|