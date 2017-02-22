---
title: "CvWriteFlag-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvWriteFlagExVA"
  - "cvmarkers/CvWriteFlagExW"
  - "cvmarkers/CvWriteFlagExVW"
  - "cvmarkers/CvWriteFlagExA"
helpviewer_keywords: 
  - "CvWriteFlagExW-Methode"
  - "CvWriteFlagExVA-Methode"
  - "CvWriteFlagExA-Methode"
  - "CvWriteFlagExVW-Methode"
ms.assetid: ee9da1e2-7b34-4cba-81e2-215d25d32e4d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvWriteFlag-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schreibt ein Flag in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.  
  
## Syntax  
  
```  
HRESULT CvWriteFlagExW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    ...  
    );  
  
HRESULT CvWriteFlagExVW(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCWSTR pMessage,  
    _In_ va_list argList);  
  
HRESULT CvWriteFlagExVA(  
    _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries,  
    _In_ CV_IMPORTANCE level,  
    _In_ int category,  
    _In_ PCSTR pMessage,  
    _In_ va_list argList);  
```  
  
#### Parameter  
 `argList`  
 Liste der Argumente.  
  
 `category`  
 Kategorie.  
  
 `level`  
 Wichtigkeitsstufe.  
  
 `pMarkerSeries`  
 Gültiger Marker\-Reihenkontext.  Darf nicht NULL sein.  
  
 `pMessage`  
 Nachrichtenformatzeichenfolge.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn die Meldung erfolgreich geschrieben wird.  Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
 **Unicode:** CvWriteFlagExW, CvWriteFlagExVW  
  
 **ANSI:** CvWriteFlagExA, CvWriteFlagExVA  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)