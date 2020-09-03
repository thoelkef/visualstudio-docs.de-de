---
title: 'IDiaEnumFrameData:: Item | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::Item method
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d0db365738e7c41c4a4e9f36b1942c5a64dedada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161258"
---
# <a name="idiaenumframedataitem"></a>IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Frame-Datenelement mithilfe eines Indexes ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 Index  
 in Der Index des [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekts, das abgerufen werden soll. Der Index liegt zwischen 0 und `count` -1, wobei `count` von der [IDiaEnumFrameData:: get_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) -Methode zurückgegeben wird.  
  
 section  
 vorgenommen Gibt ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt zurück, das das gewünschte Frame Datenelement darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
