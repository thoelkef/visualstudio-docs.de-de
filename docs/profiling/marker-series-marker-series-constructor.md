---
title: "marker_series::marker_series-Konstruktor | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::marker_series"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series-Konstruktor"
ms.assetid: 042c7d23-f1d8-4e09-9e76-a21c30243790
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::marker_series-Konstruktor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Initialisiert eine neue Instanz der `marker_series`\-Klasse.  
  
## Syntax  
  
```  
marker_series();  
marker_series(  
   _In_ LPCTSTR _SeriesName  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid  
);  
marker_series(  
   _In_ const GUID* _ProviderGuid,  
   _In_ LPCTSTR _SeriesName  
);  
```  
  
#### Parameter  
 `_SeriesName`  
 Der Name der Zeile zu erstellen.  
  
 `_ProviderGuid`  
 Die GUID des Reihenanbieters.  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [marker\_series\-Klasse](../profiling/marker-series-class.md)