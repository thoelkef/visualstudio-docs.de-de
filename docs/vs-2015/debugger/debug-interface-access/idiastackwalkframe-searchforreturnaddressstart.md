---
title: 'IDiaStackWalkFrame:: searchForReturnAddressStart | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddressStart method
ms.assetid: 47660b9b-6e4f-4dfa-88ab-63dce28f7412
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f2d34c4f10679d6f0702dead5352ddf088704b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150182"
---
# <a name="idiastackwalkframesearchforreturnaddressstart"></a>IDiaStackWalkFrame::searchForReturnAddressStart
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Durchsucht den angegebenen Stapel Rahmen nach einer Rückgabeadresse an oder in der Nähe der angegebenen Adresse.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT searchForReturnAddressStart (   
   IDiaFrameData* frame,  
   ULONGLONG      startAddress,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `frame`  
 in Ein [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) -Objekt, das den aktuellen Stapel Rahmen darstellt.  
  
 `startAddress`  
 in Eine Adresse für den virtuellen Speicher, von der aus gesucht werden soll.  
  
 `returnAddress`  
 vorgenommen Gibt die nächstgelegene Funktions Rückgabeadresse an zurück `startAddress` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
