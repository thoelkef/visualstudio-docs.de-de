---
title: 'Idiaframedata:: Get_functionparent | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aae0be22b8699bd240ed78714dd340ed14ea38e1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54992099"
---
# <a name="idiaframedatagetfunctionparent"></a>IDiaFrameData::get_functionParent
Ruft eine Schnittstelle für den Rahmen für die einschließende Funktion ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT get_functionParent (   
   IDiaFrameData** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Gibt eine [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt für die einschließende Funktion.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)