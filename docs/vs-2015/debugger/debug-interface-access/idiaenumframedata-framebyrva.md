---
title: 'Idiaenumframedata:: Framebyrva | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 825f72eec5b56fef70019b64d6e599b7c4712ee2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68146517"
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt einen Frame relative virtuelle Adresse (RVA) zurück.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 relativeVirtualAddress  
 [in] Die RVA des Frames von Interesse sind.  
  
 Rahmen  
 [out] Gibt eine [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) Objekt, das den Rahmen, die die angegebene Adresse enthält darstellt.  
  
## <a name="return-value"></a>Rückgabewert  
 Gibt bei Erfolg `S_OK` zurück. Gibt `S_FALSE` , wenn keine Framedaten die angegebene Adresse übereinstimmt. Andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
