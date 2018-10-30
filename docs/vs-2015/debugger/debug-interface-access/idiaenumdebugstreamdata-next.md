---
title: 'Idiaenumdebugstreamdata:: Next | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6e361ee151ff76334e8cf3a3c4cb9216f9ff422
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920338"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft eine angegebene Anzahl von Datensätzen in der Enumerationsfolge ab.  
  
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
 [in] Die Anzahl der Datensätze abgerufen werden sollen.  
  
 cbData  
 [in] Größe des Datenpuffers in Byte.  
  
 "pcbdata"  
 [out] Gibt die Anzahl der zurückgegebenen Bytes. Wenn `data` NULL ist, klicken Sie dann `pcbData` enthält die Gesamtzahl der Bytes an Daten zur Verfügung, für alle Datensätze angeforderten.  
  
 Daten]  
 [out] Ein Puffer, der mit der Debug-Stream-Datensatzdaten gefüllt werden soll.  
  
 pceltFetched  
 [in, out] Gibt die Anzahl der Datensätze in `data`.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`. Gibt `S_FALSE` , wenn keine weitere Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)



