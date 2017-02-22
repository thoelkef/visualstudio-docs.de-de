---
title: "marker_series::is_enabled-Methode | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled"
helpviewer_keywords: 
  - "Concurrency::diagnostic::marker_series::is_enabled-Methode"
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# marker_series::is_enabled-Methode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Bestimmt wenn eine Sitzung ist aktiviert den Anbieter.  
  
## Syntax  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### Parameter  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Kategorie.  
  
## Rückgabewert  
  
## Anforderungen  
 **Header:**  cvmarkersobj.h  
  
 **Namespace:**  Concurrency::diagnostic  
  
## Siehe auch  
 [marker\_series\-Klasse](../profiling/marker-series-class.md)