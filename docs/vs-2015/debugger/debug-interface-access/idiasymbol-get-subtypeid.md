---
title: IDiaSymbol::get_subTypeId | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 0f899920-4fc5-4de8-84a3-cd98c57bf124
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 853d0032b290f80ede23dddeae2a4b7026f63260
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428274"
---
# <a name="idiasymbolget_subtypeid"></a>IDiaSymbol::get_subTypeId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft die Untertyp-ID ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_subTypeId(   
   DWORD* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Ein Zeiger auf einen `DWORD` , der die Untertyp-ID enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
