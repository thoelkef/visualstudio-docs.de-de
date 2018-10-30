---
title: 'Idiastackwalkhelper:: Searchforreturnaddressstart | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 016f2e3ab816b7def9aa0ef1e40ef5727063eb25
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49895768"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Sucht den angegebenen Stapelrahmen für eine Absenderadresse an oder in der Nähe der Adresse angegebenen Stapel an.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `frame`  
 [in] Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) Objekt, das den aktuellen Stapelrahmen darstellt.  
  
 `startAddress`  
 [in] Eine Adresse des virtuellen Arbeitsspeichers aus dem die Suche beginnen soll.  
  
 `ReturnAddress`  
 [out] Gibt die nächste Funktion zurückgeben Adresse `startAddress`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)