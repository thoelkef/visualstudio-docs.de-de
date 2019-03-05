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
ms.openlocfilehash: eb3ef4d928aaac57f39a48e5be212c1148ef58eb
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630300"
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
 `pProvider`: durch CvInitProvider bereits initialisiertes Anbieterobjekt. Darf nicht NULL sein.

 `pSeriesName` der Markerreihenname. Darf nicht NULL sein, aber eine leere Zeichenfolge ist zulässig.

 `ppMarkerSeries`: die Adresse einer Ausgabevariablen, mit der der Markerreihenkontext gespeichert wird. Darf nicht NULL sein.

## <a name="return-value"></a>Rückgabewert
 S_OK, wenn Markerreihen erfolgreich erstellt wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.

## <a name="requirements"></a>Anforderungen
 **Header:** *cvmarkers.h*

 **Unicode:** CvCreateMarkerSeriesW

 **ANSI:** CvCreateMarkerSeriesA

## <a name="see-also"></a>Siehe auch
- [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)