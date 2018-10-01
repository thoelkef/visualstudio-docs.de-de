---
title: CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider
helpviewer_keywords:
- CvCreateDefaultMarkerSeriesOfDefaultProvider method
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4910a66481be1f00a0fd57e1a66c0756f11c6589
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47514118"
---
# <a name="cvcreatedefaultmarkerseriesofdefaultprovider-function"></a>CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion](https://docs.microsoft.com/visualstudio/profiling/cvcreatedefaultmarkerseriesofdefaultprovider-function).  
  
Erstellt Standardmarkerreihen eines Standardanbieters.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
 **Header:** cvmarkers.h  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)



