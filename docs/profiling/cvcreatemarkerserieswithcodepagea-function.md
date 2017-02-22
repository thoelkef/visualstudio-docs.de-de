---
title: "CvCreateMarkerSeriesWithCodePageA-Funktion | Microsoft Docs"
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
  - "cvmakers/CvCreateMarkerSeriesWithCodePageA"
helpviewer_keywords: 
  - "CvCreateMarkerSeriesWithCodePageA-Methode"
ms.assetid: 3d7ed601-2222-4be9-a557-f217db008753
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CvCreateMarkerSeriesWithCodePageA-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Erstellt Marker\-Reihe für einen bestimmten Anbieter und eine bestimmte Codepage.  Diese Funktion kann verwendet werden, um der Codepage für explizit den Text anzugeben, der von Markierungen API\-ANSI\-Funktionen geschrieben wird.  Die Codepage festzulegen kann nützlich sein, wenn die Ablaufverfolgung erfasst werden und auf unterschiedlichen Computern mit unterschiedlichen Gebietsschemas\/Sprachen analysiert.  Standardmäßig wird die Codepage, die von GetACP\(\) Funktion zurückgegeben wird, verwendet.  
  
## Syntax  
  
```  
HRESULT CvCreateMarkerSeriesWithCodePageA(  
   _In_ PCV_PROVIDER pProvider,  
   _In_ LPCSTR pSeriesName,  
   _In_ UINT nTextCodePage,  
   _Out_ PCV_MARKERSERIES* ppMarkerSeries  
);  
```  
  
#### Parameter  
 `pProvider`  
 Anbieterobjekt zuvor durch CvInitProvider initialisiert.  Darf nicht NULL sein.  
  
 `pSeriesName`  
 Marker\-Reihenname.  Darf nicht NULL sein, jedoch leere Zeichenfolge zulässig.  
  
 `nTextCodePage`  
 Gültige Codepage.  
  
 `ppMarkerSeries`  
 Adresse einer Ausgabevariable, die Geschäftsmarker\-Reihenkontext wird.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn Marker\-Reihe erfolgreich erstellt wird oder Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)