---
title: 'IDiaStackWalkHelper:: searchForReturnAddressStart | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper::searchForReturnAddressStart method
ms.assetid: 0a33142e-5d31-44ea-874a-a2e94d95cbd2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 706f20ee72b69eb03f3851da9af5f56e1e9b8e78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562789"
---
# <a name="idiastackwalkhelpersearchforreturnaddressstart"></a>IDiaStackWalkHelper::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Stapel Adresse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT searchForReturnAddressStart(   
   IDiaFrameData*  frame,  
   ULONGLONG       startAddress,  
   ULONGLONG*      returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `frame`  
 in Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt, das den aktuellen Stapel Rahmen darstellt.  
  
 `startAddress`  
 in Eine Adresse für den virtuellen Speicher, von der aus gesucht werden soll.  
  
 `ReturnAddress`  
 vorgenommen Gibt die nächstgelegene Funktions Rückgabeadresse an zurück `startAddress` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
