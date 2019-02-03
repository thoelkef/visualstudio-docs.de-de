---
title: 'Idiaenumdebugstreamdata:: Next | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3167df4d26cac10894a21f82faacdc0fe3590d74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55031434"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Ruft eine angegebene Anzahl von Datensätzen in der Enumerationsfolge ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 celt  
 [in] Die Anzahl der Datensätze abgerufen werden sollen.  
  
 cbData  
 [in] Größe des Datenpuffers in Byte.  
  
 pcbData  
 [out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` NULL ist, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes an Daten zur Verfügung, für alle Datensätze angeforderten.  
  
 data[]  
 [out] Ein Puffer, der mit der Debug-Stream-Datensatzdaten gefüllt werden soll.  
  
 pceltFetched  
 [in, out] Gibt die Anzahl der Datensätze in `data`.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn keine weitere Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)