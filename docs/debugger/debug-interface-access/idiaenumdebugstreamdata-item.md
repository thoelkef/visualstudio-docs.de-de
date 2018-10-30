---
title: 'Idiaenumdebugstreamdata:: Item | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Item method
ms.assetid: 761e61a5-44a6-4d5d-a98e-c2e9b89d2343
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5101c5f43e3d931a0ec4653838e4b45c01d3c5fb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936303"
---
# <a name="idiaenumdebugstreamdataitem"></a>IDiaEnumDebugStreamData::Item
Ruft den angegebenen Datensatz ab.  
  
## <a name="syntax"></a>Syntax  
  
```C++  
HRESULT Item (   
   DWORD  index,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 [in] Der Index des Datensatzes abgerufen werden sollen. Der Index befindet sich im Bereich von 0 bis `count`-1, wobei `count` von zurückgegeben wird [idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md).  
  
 cbData  
 [in] Größe des Datenpuffers in Byte.  
  
 "pcbdata"  
 [out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` ist `NULL`, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes der Daten in den angegebenen Datensatz verfügbar sind.  
  
 Daten]  
 [out] Ein Puffer, der mit der Debug-Stream-Datensatzdaten gefüllt wird.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben. Gibt `E_INVALIDARG` für ungültige Parameter und, wenn die `index` -Parameter ist außerhalb des gültigen Bereichs.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [Idiaenumdebugstreamdata:: Next](../../debugger/debug-interface-access/idiaenumdebugstreamdata-next.md)   
 [Idiaenumdebugstreams:: Item](../../debugger/debug-interface-access/idiaenumdebugstreams-item.md)   
 [Idiaenumdebugstreamdata:: Get_count](../../debugger/debug-interface-access/idiaenumdebugstreamdata-get-count.md)   
 [IDiaEnumDebugStreamData::Skip](../../debugger/debug-interface-access/idiaenumdebugstreamdata-skip.md)