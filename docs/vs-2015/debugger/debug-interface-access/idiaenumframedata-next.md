---
title: 'IDiaEnumFrameData:: Next | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Next method
ms.assetid: 546e2e23-efb2-425a-96a1-808c67c519fb
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 61fe8735511e9830542ce8622a6d984a0a817671
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161220"
---
# <a name="idiaenumframedatanext"></a>IDiaEnumFrameData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Frame-Datenelementen in der enumerationssequenz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Next (   
   ULONG           celt,   
   IDiaFrameData** rgelt,  
   ULONG*          pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 in Die Anzahl der Frame Datenelemente im Enumerator, die abgerufen werden sollen.  
  
 rgelt  
 vorgenommen Ein Array von [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekten, die mit den angeforderten Frame Datenelementen aufgefüllt werden sollen.  
  
 pceltFetched  
 vorgenommen Gibt die Anzahl der Frame Datenelemente im abgerufenen Enumerator zurück.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
