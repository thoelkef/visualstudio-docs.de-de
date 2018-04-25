---
title: 'Idiastackwalkhelper:: Searchforreturnaddressstart | Microsoft Docs'
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
ms.openlocfilehash: 5b92068c935c90e6cfe278b5f07a995c941b8a89
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
Sucht den angegebenen Stapelrahmen für eine Absenderadresse Beginn oder kurz vor dem angegebenen Stapeladresse an.  
  
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
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)