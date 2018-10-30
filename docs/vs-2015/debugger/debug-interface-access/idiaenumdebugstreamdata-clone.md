---
title: 'Idiaenumdebugstreamdata:: Clone | Microsoft-Dokumentation'
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
- IDiaEnumDebugStreamData::Clone method
ms.assetid: e7f17750-0694-4634-bf34-c821cd265c2f
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 12455a7bfede921759f0850049ee057f50cc3083
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855039"
---
# <a name="idiaenumdebugstreamdataclone"></a>IDiaEnumDebugStreamData::Clone
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Erstellt einen Enumerator, der gleiche aufgelistete Sequenz wie der aktuelle Enumerator enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumDebugStreamData** ppenum  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 ppenum  
 [out] Gibt eine [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md) -Objekt, das die doppelt vorhandenen Sequenz von Debug-Stream Datensätzen enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)



