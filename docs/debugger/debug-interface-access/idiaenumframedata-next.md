---
title: 'Idiaenumframedata:: Next | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6835cda6c8c2a5cb20135abf92a523a270b32c78
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
Ruft eine angegebene Anzahl von Datenelementen in die Enumerationsfolge Frame ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Frames-Datenelemente im Enumerator abgerufen werden sollen.  
  
 rgelt  
 [out] Ein Array von [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekten, die mit der angeforderten Daten Frameelemente ausgefüllt werden.  
  
 pceltFetched  
 [out] Gibt die Anzahl der Frames-Datenelemente in der abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` , wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)