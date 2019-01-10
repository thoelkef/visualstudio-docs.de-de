---
title: 'Idialoadcallback2:: Restrictdbgaccess | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaLoadCallback2::RestrictDBGAccess method
ms.assetid: 63b67a93-2910-4fff-aa70-6b2eaa08e5c8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8238469232656d4fa32b71fbfb7704afd6870b54
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843855"
---
# <a name="idialoadcallback2restrictdbgaccess"></a>IDiaLoadCallback2::RestrictDBGAccess
Bestimmt, ob die Suche nach Informationen zum Debuggen von .dbg-Dateien zulässig ist.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT RestrictDBGAccess();  
```  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Ein Rückgabewert als `S_OK` zum Verhindern der Suche nach Informationen zum Debuggen von .dbg-Dateien.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)