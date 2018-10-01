---
title: marker_series::is_enabled-Methode | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic::marker_series::is_enabled
helpviewer_keywords:
- Concurrency::diagnostic::marker_series::is_enabled method
ms.assetid: 8ce4dd50-ca29-4c72-98d6-582693f7d501
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db5a91a3b2212967cb1de915f15abb9d5caa9d98
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513283"
---
# <a name="markerseriesisenabled-method"></a>marker_series::is_enabled-Methode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [marker_series:: is_enabled-Methode](https://docs.microsoft.com/visualstudio/profiling/marker-series-is-enabled-method).  
  
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



