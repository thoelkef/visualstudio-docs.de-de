---
title: "marker_series::write_flag-Methode | Microsoft Docs"
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
  - "cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::write_flag-Methode"
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::write_flag-Methode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schreibt ein Flag in die Parallelitätsschnellansichts\-Ablaufverfolgungsdatei.  
  
## Syntax  
  
```  
void write_flag(  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
void write_flag(  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### Parameter  
 `_Format`  
 Eine kombinierte Formatzeichenfolge, die Text vermischte mit null\) enthält oder mehr Formatelementen, die den Objekten in der Argumentliste entsprechen.  
  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Kategorie.  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [marker\_series\-Klasse](../profiling/marker-series-class.md)