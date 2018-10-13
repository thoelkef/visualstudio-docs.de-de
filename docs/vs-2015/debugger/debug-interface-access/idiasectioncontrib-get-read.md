---
title: 'Idiasectioncontrib:: Get_read | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_read method
ms.assetid: 68bfb35c-eabd-412a-bc8f-3094703b98c4
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9460fdd37b53f9e3710bb466e3a06697158aabc9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188369"
---
# <a name="idiasectioncontribgetread"></a>IDiaSectionContrib::get_read
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag, das angibt, ob der Abschnitt gelesen werden kann.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT get_read (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt `TRUE` Wenn Abschnitt gelesen werden kann; andernfalls `FALSE`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` Wenn diese Eigenschaft nicht unterstützt wird. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)



