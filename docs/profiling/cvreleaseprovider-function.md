---
title: CvReleaseProvider-Funktion | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvReleaseProvider
helpviewer_keywords:
- CvReleaseProvider method
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f0b54fc676a9e7e6ee523bba7f94f58aef49916b
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
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