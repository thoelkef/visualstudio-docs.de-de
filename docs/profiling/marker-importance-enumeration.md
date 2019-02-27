---
title: marker_importance Enumeration | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_importance
helpviewer_keywords:
- Concurrency::diagnostic::marker_importance enumeration
ms.assetid: d5524ea0-0227-4d8e-9122-332291042df5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b3f5cfb583ec4fceb9fb7428b08c00f6ca8e26b6
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56613894"
---
# <a name="markerimportance-enumeration"></a>marker_importance-Enumeration
Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.

## <a name="syntax"></a>Syntax

```cpp
enum marker_importance;
```

## <a name="members"></a>Member

### <a name="values"></a>Werte

|name|Beschreibung|
|----------|-----------------|
|`critical_importance`|Gibt an, dass der Marker kritisch wichtig ist|
|`high_importance`|Gibt an, dass der Marker hoch wichtig ist|
|`low_importance`|Gibt an, dass der Marker weniger wichtig ist|
|`normal_importance`|Gibt an, dass der Marker normal wichtig ist|

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [diagnostic-Namespace](../profiling/diagnostic-namespace.md)