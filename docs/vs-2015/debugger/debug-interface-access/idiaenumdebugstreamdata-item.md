---
title: 'Idiaenumdebug bugstreamdata:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4b80f71b2ca5d718f2de834389b4caab728e1f1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197887"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den angegebenen Datensatz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 in Der Index des abzurufenden Datensatzes. Der Index liegt zwischen 0 und `count` -1, wobei `count` von [idiaenumdebug bugstreamdata:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)zurückgegeben wird.  
  
 cbData  
 in Größe des Daten Puffers in Bytes.  
  
 pcbData  
 vorgenommen Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` ist `NULL` , `pcbData` enthält die Gesamtanzahl der Daten bytes, die im angegebenen Datensatz verfügbar sind.  
  
 data[]  
 vorgenommen Ein Puffer, der mit den Daten des Debug-Datensatzes aufgefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` für ungültige Parameter und zurück `index` , wenn der Parameter außerhalb des gültigen Bereichs liegt.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebug bugstreamdata:: Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebug:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebug bugstreamdata:: get_Count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)
