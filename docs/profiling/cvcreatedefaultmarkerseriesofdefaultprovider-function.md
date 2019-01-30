---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 036eba6fd1c25b475b703f49e1841c647d5fbd9a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962169"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion
Erstellt Standardmarkerreihen eines Standardanbieters.  
  
## <a name="syntax"></a>Syntax  
  
```C  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `ppProvider`  
 Adresse der Anbieterobjektvariable. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.  
  
 `ppMarkerSeries`  
 Adresse der Markerreihenobjektvariable. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn Anbieter und Markerreihen erfolgreich erstellt wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** *cvmarkers.h*  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)