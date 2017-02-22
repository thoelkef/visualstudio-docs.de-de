---
title: "marker_series::write_alert-Methode | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert"
helpviewer_keywords: 
  - "Concurrency::diagnostic:marker_series::write_alert-Methode"
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_alert-Methode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schreibt eine Warnung in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.  
  
## Syntax  
  
```  
void write_alert(  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parameter  
 `_Format`  
 Eine kombinierte Formatzeichenfolge, die Text vermischte mit null\) enthält oder mehr Formatelementen, die den Objekten in der Argumentliste entsprechen.  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [marker\_series\-Klasse](../profiling/marker-series-class.md)