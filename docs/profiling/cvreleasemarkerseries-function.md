---
title: CvReleaseMarkerSeries-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d28041defb536c01d4e71d38f7eddb18dc2d709f
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries-Funktion
Gibt Markerreihen frei. Verwenden Sie keine freigegebenen Markerreihenobjekte, da die Anwendung andernfalls möglicherweise abstürzt. Wenn Markerreihen nicht freigegeben werden, führt dies zu einem Arbeitsspeicherverlust.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pMarkerSeries`  
 Adresse der Anbieterobjektvariable. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn Markerreihen erfolgreich freigegeben wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkers.h  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)