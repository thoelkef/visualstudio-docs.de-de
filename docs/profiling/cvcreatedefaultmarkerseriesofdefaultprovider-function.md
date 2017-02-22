---
title: "CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion | Microsoft Docs"
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
  - "cvmarkers/CvCreateDefaultMarkerSeriesOfDefaultProvider"
helpviewer_keywords: 
  - "CvCreateDefaultMarkerSeriesOfDefaultProvider-Methode"
ms.assetid: 24eb80f8-8fca-4c47-93b5-bb1eb8ffdffd
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateDefaultMarkerSeriesOfDefaultProvider-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt Standardmarkerreihen eines Standardanbieters.  
  
## Syntax  
  
```  
HRESULT CvCreateDefaultMarkerSeriesOfDefaultProvider(  
   _Out_ PCV_PROVIDER* ppProvider,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parameter  
 `ppProvider`  
 Adresse der Anbieterobjektvariable.  Adresse kann NULL sein, die Variable kann keinen Wert verfügen.  
  
 `ppMarkerSeries`  
 Adresse der Marker\-Reihenobjektvariable.  Adresse kann NULL sein, die Variable kann keinen Wert verfügen.  
  
## Rückgabewert  
 S\_OK, wenn Anbieter\- und Marker\-Reihe erfolgreich erstellt wird oder Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)