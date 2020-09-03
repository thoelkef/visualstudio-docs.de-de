---
title: CvCreateMarkerSeries-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dc4af6ef3b2ffc89ec0e69a6dd63923f5c55ffe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155536"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt Markerreihen für einen angegebenen Anbieter.  
  
## <a name="syntax"></a>Syntax  
  
```  
_Check_return_ HRESULT CvCreateMarkerSeriesW(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCWSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
  
_Check_return_ HRESULT CvCreateMarkerSeriesA(  
    _In_ PCV_PROVIDER  pProvider,  
    _In_ LPCSTR pSeriesName,  
    _Out_ PCV_MARKERSERIES* ppMarkerSeries);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProvider`  
 Durch CvInitProvider bereits initialisiertes Anbieterobjekt. Darf nicht NULL sein.  
  
 `pSeriesName`  
 Markerreihenname. Darf nicht NULL sein, aber eine leere Zeichenfolge ist zulässig.  
  
 `ppMarkerSeries`  
 Adresse einer Ausgabevariablen, mit der Markerreihenkontext gespeichert wird. Darf nicht NULL sein.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn Markerreihen erfolgreich erstellt wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Weitere Informationen  
 [C++-Bibliotheks Referenz](../profiling/cpp-library-reference.md)
