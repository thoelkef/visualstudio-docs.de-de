---
title: diagnostic-Namespace | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic
helpviewer_keywords:
- Concurrency::diagnostic namespace
ms.assetid: ad786b19-7c4c-46ee-bfb6-c4752b373a09
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03671f314dca3c016f9524bcb246b74e0eb1f837
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62970082"
---
# <a name="diagnostic-namespace"></a>Diagnostic-Namespace
Der `diagnostics`-Namespace stellt Funktionen zum Ausgeben von Markern für Nebenläufigkeitsschnellansichten bereit.

## <a name="syntax"></a>Syntax

```cpp
namespace diagnostic;
```

## <a name="members"></a>Member

### <a name="classes"></a>Klassen

|name|Beschreibung|
|----------|-----------------|
|[marker_series-Klasse](../profiling/marker-series-class.md)|Stellt einen seriellen Kanal mit Ereignissen dar, die von einem einzelnen Anbieter generiert werden.|
|[span-Klasse](../profiling/span-class.md)|Definiert eine Phase der Anwendung.|

### <a name="enumerations"></a>Enumerationen

|name|Beschreibung|
|----------|-----------------|
|[marker_importance-Enumeration](../profiling/marker-importance-enumeration.md)|Stellt die Wichtigkeitsstufe eines Markers für die Nebenläufigkeitsschnellansicht dar.|

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Parallelität

## <a name="see-also"></a>Siehe auch
- [Concurrency-Namespace (Parallelitätsschnellansicht)](../profiling/concurrency-namespace-concurrency-visualizer.md)