---
title: IDiaSymbol::get_memorySpaceKind | Microsoft-Dokumentation
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
ms.assetid: 9a63b298-8577-4c15-8595-530558d41bf1
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 73d50d24b473d834d9bc4c6c36eb5a0507d6fccb
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51774743"
---
# <a name="idiasymbolgetmemoryspacekind"></a>IDiaSymbol::get_memorySpaceKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Art der Speicher-Speicherplatz ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_memorySpaceKind(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 [out] Ein Zeiger auf eine `DWORD` , die die Art der Speicher-Speicherplatz enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` oder ein Fehlercode.  
  
## <a name="see-also"></a>Siehe auch  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)



