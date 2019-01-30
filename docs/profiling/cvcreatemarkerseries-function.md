---
title: CvCreateMarkerSeries-Funktion | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkers/CvCreateMarkerSeriesA
- cvmarkers/CvCreateMarkerSeriesW
helpviewer_keywords:
- CvCreateMarkerSeriesA method
- CvCreateMarkerSeriesW method
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a0c0371992bde7b7ac58551457fa81e2b18a8f56
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55006983"
---
# <a name="cvcreatemarkerseries-function"></a>CvCreateMarkerSeries-Funktion
Erstellt Markerreihen für einen angegebenen Anbieter.  
  
## <a name="syntax"></a>Syntax  
  
```C  
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
 **Header:** *cvmarkers.h*  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)