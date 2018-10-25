---
title: 'Idiaframedata:: Get_functionparent | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_functionParent method
ms.assetid: f00b9ab1-d4da-4818-973a-58f8f0e66769
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e2b7a920944d748cdd1f56b56257e3d895cfc06b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923549"
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