---
title: CvReleaseProvider-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d5e611c2a964fcbb78a387a09989436e672ecd6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551233"
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt Markeranbieter frei. Die Freigabe des Markeranbieters hat keine Auswirkungen auf bereits erstellte Markerreihen dieses Anbieters. Markerreihen müssen durch den Aufruf von CvReleaseMarkerSeries getrennt freigegeben werden. Wenn Markeranbieter nicht freigegeben werden, führt dies zu einem Arbeitsspeicherverlust.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProvider`  
 Anbieterkontext. Darf nicht NULL sein.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn der Anbieter erfolgreich freigegeben wurde, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkers.h  
  
## <a name="see-also"></a>Weitere Informationen  
 [C++-Bibliotheks Referenz](../profiling/cpp-library-reference.md)
