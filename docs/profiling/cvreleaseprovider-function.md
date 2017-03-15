---
title: "CvReleaseProvider-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvReleaseProvider"
helpviewer_keywords: 
  - "CvReleaseProvider-Methode"
ms.assetid: 8d74379e-295d-452b-bd5f-0769df387d4f
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvReleaseProvider-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt Markeranbieter frei.  Für das Freigeben des Markeranbieters beeinflusst nicht zuvor erstellte Markerreihen dieses Anbieters.  Marker\-Reihe muss Version von CvReleaseMarkerSeries\-Aufruf getrennt sein.  Fehler, Anbieterursachen freizugeben ein Speicherverlust.  
  
## Syntax  
  
```  
HRESULT CvReleaseProvider(  
   _In_ PCV_PROVIDER pProvider  
);  
```  
  
#### Parameter  
 `pProvider`  
 Anbieterkontext.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn Anbieter erfolgreich freigegeben werden oder Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)