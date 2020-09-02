---
title: 'Idiaenumdebug bugstreamdata:: Next | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bdbf58321426890bffd45a08818dc5341bdfc3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187398"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Datensätzen in der enumerationssequenz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
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
 in Die Anzahl der Datensätze, die abgerufen werden sollen.  
  
 cbData  
 in Größe des Daten Puffers in Bytes.  
  
 pcbData  
 vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` NULL ist, `pcbData` enthält die Gesamtanzahl der Daten bytes, die für alle angeforderten Datensätze verfügbar sind.  
  
 data[]  
 vorgenommen Ein Puffer, der mit den Daten des Debug-Datensatzes aufgefüllt werden soll.  
  
 pceltFetched  
 [in, out] Gibt die Anzahl der Datensätze in zurück `data` .  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt zurück, `S_FALSE` Wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)
