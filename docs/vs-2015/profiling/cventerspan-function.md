---
title: CvEnterSpan-Funktion | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- cvmarkers/CvEnterSpanVA
- cvmarkers/CvEnterSpanW
- cvmarkers/CvEnterSpanExW
- cvmarkers/CvEnterSpanA
- cvmarkers/CvEnterSpanExVW
- cvmarkers/CvEnterSpanExA
- cvmarkers/CvEnterSpanVW
helpviewer_keywords:
- CvEnterSpanVW method
- CvEnterSpanVA method
- CvEnterSpanExA method
- CvEnterSpanW method
- CvEnterSpanA method
- CvEnterSpanExVW method
- CvEnterSpanExW method
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 40031567b5339803ccfa7f4a5b3db4f006c6c134
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193225"
---
# <a name="cventerspan-function"></a>CvEnterSpan-Funktion
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kennzeichnet den Anfang einer neuen Spanne.  
  
## <a name="syntax"></a>Syntax  
  
```  
HRESULT CvEnterSpanW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    ...   
    );   
  
HRESULT CvEnterSpanA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,  
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList  
    );   
  
HRESULT CvEnterSpanExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    ...   
    );   
  
HRESULT CvEnterSpanExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCWSTR pMessage,   
    _In_ va_list argList);   
  
HRESULT CvEnterSpanExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,   
    _In_ CV_IMPORTANCE level,   
    _In_ int category,   
    _Out_ PCV_SPAN* ppSpan,   
    _In_ PCSTR pMessage,   
    _In_ va_list argList);  
  
```  
  
#### <a name="parameters"></a>Parameter  
 `argList`  
 Liste von Argumenten.  
  
 `category`  
 Kategorie der Spanne.  
  
 `level`  
 Wichtigkeitsstufe der Spanne.  
  
 `pMarkerSeries`  
 Gültiger Markerreihenkontext. Darf nicht NULL sein.  
  
 `pMessage`  
 Formatzeichenfolge für die Meldung. Darf nicht NULL sein.  
  
 `ppSpan`  
 Adresse der Variablen, in der das resultierende span-Objekt gespeichert wird. Die Adresse darf nicht NULL sein. Die Variable kann einen beliebigen Wert aufweisen.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn die Meldung erfolgreich geschrieben wurde. Fehlercode, wenn Fehler aufgetreten sind. Prüfen Sie mit den Makros SUCCEEDED bzw. FAILED, ob Fehler vorliegen.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkers.h  
  
 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW  
  
 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW  
  
## <a name="see-also"></a>Weitere Informationen  
 [C++-Bibliotheks Referenz](../profiling/cpp-library-reference.md)
