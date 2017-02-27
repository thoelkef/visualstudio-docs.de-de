---
title: "CvEnterSpan-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvEnterSpanVA"
  - "cvmarkers/CvEnterSpanW"
  - "cvmarkers/CvEnterSpanExW"
  - "cvmarkers/CvEnterSpanA"
  - "cvmarkers/CvEnterSpanExVW"
  - "cvmarkers/CvEnterSpanExA"
  - "cvmarkers/CvEnterSpanVW"
helpviewer_keywords: 
  - "CvEnterSpanVW-Methode"
  - "CvEnterSpanVA-Methode"
  - "CvEnterSpanExA-Methode"
  - "CvEnterSpanW-Methode"
  - "CvEnterSpanA-Methode"
  - "CvEnterSpanExVW-Methode"
  - "CvEnterSpanExW-Methode"
ms.assetid: 91689e9c-6733-44b9-b36a-8b9b2eef7d1d
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvEnterSpan-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Markiert den Beginn einer neuen Spanne.  
  
## Syntax  
  
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
  
#### Parameter  
 `argList`  
 Liste der Argumente.  
  
 `category`  
 Kategorie der Spanne  
  
 `level`  
 Wichtigkeitsstufe der Spanne.  
  
 `pMarkerSeries`  
 Gültiger Marker\-Reihenkontext.  Darf nicht NULL sein.  
  
 `pMessage`  
 Nachrichtenformatzeichenfolge.  Darf nicht NULL sein.  
  
 `ppSpan`  
 Adresse der Variablen, die resultierendes Spannenobjekt enthält.  Adresse kann NULL sein, die Variable kann keinen Wert verfügen.  
  
## Rückgabewert  
 S\_OK, wenn die Meldung erfolgreich geschrieben wird.  Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
 **Unicode:** CvEnterSpanW, CvEnterSpanVW, CvEnterSpanExW, CvEnterSpanExVW  
  
 **ANSI:** CvEnterSpanA, CvEnterSpanVA, CvEnterSpanExA, CvEnterSpanExVW  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)