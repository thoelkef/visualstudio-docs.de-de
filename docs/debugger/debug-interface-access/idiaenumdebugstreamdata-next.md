---
title: 'Idiaenumdebugstreamdata:: Next | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac3e4e59f96c1178a57dbcb7b936a69905fa265d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
Ruft eine angegebene Anzahl von Datensätzen in der aufgelisteten Sequenz ab.  
  
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
 [in] Die Größe des Datenpuffers in Bytes.  
  
 pcbData  
 [out] Gibt die Anzahl der zurückgegebenen Bytes zurück. Wenn `data` NULL ist, klicken Sie dann `pcbData` die Gesamtanzahl der Bytes der Daten verfügbar für alle Datensätze angeforderten enthält.  
  
 Daten]  
 [out] Ein Puffer, die mit der Debug-datenstromdaten Datensatz gefüllt werden soll.  
  
 pceltFetched  
 [in, out] Gibt die Anzahl der Datensätze in `data`.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`. Gibt `S_FALSE` , wenn keine weiteren Datensätze vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)