---
title: PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 33ebaa31-0a35-47d5-a4e3-afd83e16f53e
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1285e4efa3db8a7ec99808f5888d3dbf948e589
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152521"
---
# <a name="profilerheapobjectscopelist-structure"></a>PROFILER_HEAP_OBJECT_SCOPE_LIST-Struktur
Diese Struktur ist nur Funktionsobjekten zugeordnet. Die Bereichsliste stellt den Schließvorgang für die Funktion als Liste von Bereichen dar, wobei jeder Bereich ein Heapobjekt mit einer zugeordneten Eigenschaftenliste ist, die Variablen in jedem angegebenen Bereich darstellt. In einigen Fällen ist die Namen der Objekte im Bereich stehen möglicherweise nicht zur Verfügung, und nur deren Index in der Liste verfügbar.  
  
## <a name="syntax"></a>Syntax  
  
```cpp
typedef struct _PROFILER_HEAP_OBJECT_SCOPE_LIST{    UINT count;    [size_is(count)] PROFILER_HEAP_OBJECT_ID scopes[];} PROFILER_HEAP_OBJECT_SCOPE_LIST;  
```  
  
## <a name="members"></a>Member  
  
|Member|Typ|Beschreibung|  
|------------|----------|-----------------|  
|count|UINT|Die Anzahl der Bereiche|  
|scopes|[PROFILER_HEAP_OBJECT_ID-Typ](../../winscript/reference/profiler-heap-object-id-type.md)|Ein Array von Bereichen.|