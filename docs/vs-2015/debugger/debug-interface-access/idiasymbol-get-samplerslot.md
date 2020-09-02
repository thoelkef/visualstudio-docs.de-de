---
title: 'Idiasymmetribol:: get_samplerSlot | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 41c751ba-81be-4bd3-838f-8373fc146157
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5f63272f3824c801deb71f974f144e692b673cf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62431393"
---
# <a name="idiasymbolget_samplerslot"></a>IDiaSymbol::get_samplerSlot
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft den samplingslot ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_samplerSlot(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Ein Zeiger auf einen `DWORD` , der den samplingslot enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
