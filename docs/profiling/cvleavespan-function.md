---
title: "CvLeaveSpan-Funktion | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cvmarkers/CvLeaveSpan"
helpviewer_keywords: 
  - "CvLeaveSpan-Methode"
ms.assetid: 3bf65fdf-a471-4efd-ac7a-03e701bbae5d
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# CvLeaveSpan-Funktion
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Markiert das Ende der Spanne.  
  
## Syntax  
  
```  
HRESULT CvLeaveSpan(  
   _In_ PCV_SPAN pSpan  
);  
```  
  
#### Parameter  
 `pSpan`  
 Überspannen Sie das Objekt, das vom vorherigen Aufruf CvEnterSpan\* zurückgegeben wird.  Darf nicht NULL sein.  
  
## Rückgabewert  
 S\_OK, wenn die Meldung erfolgreich geschrieben wird.  Fehlercode, sofern dieses alle Fehler auftritt.  Makros der Verwendung SUCCEEDED\/FAILED, auf dem Fehlerzustand zu überprüfen.  
  
## Anforderungen  
 **Header:**  cvmarkers.h  
  
## Siehe auch  
 [C\+\+\-Bibliotheksreferenz](../profiling/cpp-library-reference.md)