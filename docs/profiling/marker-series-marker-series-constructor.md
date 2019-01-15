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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8fad8eec19346273a7ea302da4653faa1bdec032
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53987232"
---
# <a name="markerseriesmarkerseries-constructor"></a>marker_series:: marker_series-Konstruktor
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
 `_SeriesName`  
 Der Name der zu erstellenden Reihe  
  
 `_ProviderGuid`  
 Die GUID des Anbieters der Reihe  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *cvmarkersobj.h*  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [marker_series-Klasse](../profiling/marker-series-class.md)