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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46fc321dac1d8e750e1b5eb23516a4ea0a3e9a1e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51750512"
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



