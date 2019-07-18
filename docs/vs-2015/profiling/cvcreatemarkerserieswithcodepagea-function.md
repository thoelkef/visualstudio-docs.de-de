---
title: CvCreateMarkerSeriesWithCodePageA-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmakers/CvCreateMarkerSeriesWithCodePageA
helpviewer_keywords:
- CvCreateMarkerSeriesWithCodePageA method
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 635a872372ab775eceb00854a616884f3fc19fef
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155532"
---
# <a name="cvcreatemarkerserieswithcodepagea-function"></a>CvCreateMarkerSeriesWithCodePageA-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Erstellt Markerreihen für einen angegebenen Anbieter und eine angegebene Codepage. Mit dieser Funktion kann die Codepage für den von Marker-API-ANSI-Funktionen ausgeschriebenen Text explizit angegeben werden. Das Festlegen der Codepage kann in Fällen nützlich sein, in denen die Ablaufverfolgung aufgezeichnet und anschließend auf unterschiedlichen Computern mit unterschiedlichen Gebietsschemas/Sprachen analysiert wird. Standardmäßig wird die von der GetACP()-Funktion zurückgegebene Codepage verwendet.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pProvider`  
 Durch CvInitProvider bereits initialisiertes Anbieterobjekt. Darf nicht NULL sein.  
  
 `pSeriesName`  
 Markerreihenname. Darf nicht NULL sein, aber eine leere Zeichenfolge ist zulässig.  
  
 `nTextCodePage`  
 Gültige Codepage.  
  
 `ppMarkerSeries`  
 Adresse einer Ausgabevariablen, mit der Markerreihenkontext gespeichert wird. Darf nicht NULL sein.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn Markerreihen erfolgreich erstellt wurden, oder Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Header:** cvmarkers.h  
  
## <a name="see-also"></a>Siehe auch  
 [C++-Bibliotheksreferenz](../profiling/cpp-library-reference.md)
