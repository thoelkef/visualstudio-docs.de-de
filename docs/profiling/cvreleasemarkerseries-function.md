---
title: CvReleaseMarkerSeries-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseMarkerSeries
helpviewer_keywords:
- CvReleaseMarkerSeries method
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 51ef7cc83c876f5ac9031010fd45e2230e6c4c03
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006998"
---
# <a name="cvreleasemarkerseries-function"></a>CvReleaseMarkerSeries-Funktion
Gibt Markerreihen frei. Verwenden Sie keine freigegebenen Markerreihenobjekte, da die Anwendung andernfalls möglicherweise abstürzt. Wenn Markerreihen nicht freigegeben werden, führt dies zu einem Arbeitsspeicherverlust.  
  
## <a name="syntax"></a>Syntax  
  
```C  
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
 **Header:** *cvmarkers.h*  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)