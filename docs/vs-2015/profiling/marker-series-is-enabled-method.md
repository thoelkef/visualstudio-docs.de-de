---
title: marker_series::is_enabled-Methode | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9ccef8ebbf63835a71027643b518280d5f4f867b
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/19/2019
ms.locfileid: "54797951"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled-Methode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bestimmt, ob eine Sitzung den Anbieter aktiviert hat  
  
## <a name="syntax"></a>Syntax  
  
```  
bool is_enabled();  
bool is_enabled(  
   marker_importance _Importance,  
   int _Category  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `_Importance`  
 Wichtigkeitsstufe.  
  
 `_Category`  
 Kategorie.  
  
## <a name="return-value"></a>Rückgabewert  
  
## <a name="requirements"></a>Anforderungen  
 **Header:** cvmarkersobj.h  
  
 **Namespace:** Concurrency::diagnostic  
  
## <a name="see-also"></a>Siehe auch  
 [marker_series-Klasse](../profiling/marker-series-class.md)
