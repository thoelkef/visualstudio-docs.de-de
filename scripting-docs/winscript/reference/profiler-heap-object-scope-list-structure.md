---
title: PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur | Microsoft Docs
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67f0972faee11e15bd5d0e9a219e439df49d9672
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur
Diese Struktur ist nur Funktionsobjekten zugeordnet. Die Bereichsliste stellt den Schließvorgang für die Funktion als Liste von Bereichen dar, wobei jeder Bereich ein Heapobjekt mit einer zugeordneten Eigenschaftenliste ist, die Variablen in jedem angegebenen Bereich darstellt. In einigen Fällen ist die Namen der Objekte im Gültigkeitsbereich u. u. nicht verfügbar, und nur ihre Index in der Eigenschaftenliste verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```  
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Member  
  
|Member|Typ|Beschreibung|  
|------------|----------|-----------------|  
|count|UINT|Die Anzahl der Bereiche|  
|scopes|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Ein Array von Bereichen.|