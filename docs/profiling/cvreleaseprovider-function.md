---
title: CvReleaseProvider-Funktion | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 6cd65b5b90112e42c4503a650baa4a362b020566
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="cvreleaseprovider-function"></a>CvReleaseProvider-Funktion
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
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)