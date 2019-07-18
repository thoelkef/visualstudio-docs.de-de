---
title: marker_series::write_flag-Methode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersojb/Concurrency::diagnostic::marker_series::write_flag
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::write_flag method
ms.assetid: ca07f388-e5d5-46fd-b991-fe6e9029a68f
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b44c7cf2d2eb0f538b3819265298f1ca4166e6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200750"
---
# <a name="markerserieswriteflag-method"></a>marker_series::write_flag-Methode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Schreibt ein Flag in die Ablaufverfolgungsdatei der Nebenläufigkeitsschnellansicht  
  
## <a name="syntax"></a>Syntax  
  
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
  
#### <a name="parameters"></a>Parameter  
 `_Format`  
 Eine zusammengesetzte Formatzeichenfolge mit Text, der 0 oder mehr Formatelemente enthält, die Objekten in der Argumentliste entsprechen.  
  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Kategorie.  
  
## <a name="requirements"></a>Requirements (Anforderungen)  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [marker_series-Klasse](../profiling/marker-series-class.md)
