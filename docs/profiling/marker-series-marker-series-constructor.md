---
title: marker_series::marker_series-Konstruktor | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series
helpviewer_keywords:
- Concurrency::diagnostic::marker_series constructor
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5178b2cebdfa4246256aef6334e026ef091fa553
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831412"
---
# <a name="marker_seriesmarker_series-constructor"></a>marker_series:: marker_series-Konstruktor
Initialisiert eine neue Instanz der `marker_series`-Klasse.

## <a name="syntax"></a>Syntax

```cpp
marker_series();
marker_series(
   _In_ LPCTSTR _SeriesName
);
marker_series(
   _In_ const GUID* _ProviderGuid
);
marker_series(
   _In_ const GUID* _ProviderGuid,
   _In_ LPCTSTR _SeriesName
);
```

#### <a name="parameters"></a>Parameter
 `_SeriesName`: der Name der zu erstellenden Reihe.

 `_ProviderGuid` die GUID des Anbieters der Reihe.

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkersobj.h*

 **Namespace:** Concurrency::diagnostic

## <a name="see-also"></a>Siehe auch
- [marker_series-Klasse](../profiling/marker-series-class.md)