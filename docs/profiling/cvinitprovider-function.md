---
title: "CvInitProvider-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvInitProvider"
helpviewer_keywords: 
  - "CvInitProvider-Methode"
ms.assetid: ba1863ad-e35f-4d34-a2f2-5e68957d1915
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvInitProvider-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Initialisiert Markeranbieter.  Dürfen vor allen anderen SDK\-Funktionen Parallelitätsschnellansicht aufgerufen werden.  
  
## Syntax  
  
```  
HRESULT CvInitProvider(  
   _In_ const GUID* pGuid,  
   _Out_ PCV_PROVIDER* ppProvider  
);  
```  
  
#### Parameter  
 `pGuid`  
 Anbieter\-GUID.  Darf nicht NULL sein.  
  
 `ppProvider`  
 Adresse einer Ausgabevariable, die Anbieterkontext speichert.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn Anbieter erfolgreich initialisiert wird Fehlercode oder, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)