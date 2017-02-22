---
title: "CvReleaseMarkerSeries-Funktion | Microsoft Docs"
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
  - "cvmarkers/CvReleaseMarkerSeries"
helpviewer_keywords: 
  - "CvReleaseMarkerSeries-Methode"
ms.assetid: 3b4711ee-e534-411d-9128-f69cd7932a48
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvReleaseMarkerSeries-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Marker\-Reihe frei.  Verwenden Sie nicht Marker\-Reihe, die möglicherweise Objekt, nachdem es andernfalls die Anwendung freigegeben wurde, Ausführen.  Fehler, Marker\-Reihe freizugeben verursacht einen Speicherverlust.  
  
## Syntax  
  
```  
HRESULT CvReleaseMarkerSeries(  
   _In_reads_bytes_(16) PCV_MARKERSERIES pMarkerSeries  
);  
```  
  
#### Parameter  
 `pMarkerSeries`  
 Adresse der Anbieterobjektvariable.  Adresse kann NULL sein, die Variable kann keinen Wert verfügen.  
  
## Rückgabewert  
 S\_OK, wenn Marker\-Reihe erfolgreich freigegeben werden oder Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)