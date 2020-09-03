---
title: 'Idiasymmetribol:: get_isReturnValue | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 37aaf48a-65cb-4ec2-823e-1c637a9f939c
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a68fbab2486cba00fdc4f24c7092c207a85b815
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151521"
---
# <a name="idiasymbolget_isreturnvalue"></a>IDiaSymbol::get_isReturnValue
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Gibt an, ob die Variable einen Rückgabewert enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_isReturnValue(   
   BOOL* pRetVal);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Ein Zeiger auf einen- `BOOL` Wert, der angibt, ob die Variable einen Rückgabewert enthält.  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
