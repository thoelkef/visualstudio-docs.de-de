---
title: "span::span-Konstruktor | Microsoft Docs"
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
  - "cvmarkersobj/Concurrency::diagnostic::span::span"
helpviewer_keywords: 
  - "Concurrency::diagnostic::span-Konstruktor"
ms.assetid: 8b5578aa-5e5c-4ac7-87c7-ce87c4246e2c
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# span::span-Konstruktor
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Initialisiert eine neue Instanz der `span`-Klasse.  
  
## <a name="syntax"></a>Syntax  
  
```  
span(  
   const marker_series& _Series,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
span(  
   const marker_series& _Series,  
   marker_importance _Importance,  
   int _Category,  
   _In_ LPCTSTR _Format,  
   ...  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `_Series`  
 Gültige Marker Reihe Kontext.  
  
 `_Format`  
 Eine kombinierte Formatzeichenfolge, die Text enthält, vermischt mit 0 (null) oder mehr Formatelementen, die Objekten in der Argumentliste entsprechen.  
  
 `_Importance`  
 Wichtigkeit.  
  
 `_Category`  
 Kategorie.  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency:: Diagnostic
 
 ## <a name="see-also"></a>Siehe auch
 [Span-Klasse](../profiling/span-class.md)