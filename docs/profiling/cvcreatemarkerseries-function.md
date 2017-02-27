---
title: "CvCreateMarkerSeries-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvCreateMarkerSeriesA"
  - "cvmarkers/CvCreateMarkerSeriesW"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesA-Methode"
  - "CvCreateMarkerSeriesW-Methode"
ms.assetid: e280530b-137a-43a7-8643-aa514ab86ed7
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvCreateMarkerSeries-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt Marker\-Reihe für einen bestimmten Anbieter.  
  
## Syntax  
  
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
  
#### Parameter  
 `pProvider`  
 Anbieterobjekt zuvor durch CvInitProvider initialisiert.  Darf nicht NULL sein.  
  
 `pSeriesName`  
 Marker\-Reihenname.  Darf nicht NULL sein, jedoch leere Zeichenfolge zulässig.  
  
 `ppMarkerSeries`  
 Adresse einer Ausgabevariable, die Geschäftsmarker\-Reihenkontext wird.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn Marker\-Reihe erfolgreich erstellt wird oder Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
 **Unicode:** CvCreateMarkerSeriesW  
  
 **ANSI:** CvCreateMarkerSeriesA  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)