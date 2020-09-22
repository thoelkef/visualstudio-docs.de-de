---
title: 'Idiasymmetribol:: get_hasInlAsm | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_hasInlAsm method
ms.assetid: 7001c7cc-1459-4929-851b-a08066a803c6
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ec115e56a4eb4aff887e7683c261853c729441bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841154"
---
# <a name="idiasymbolget_hasinlasm"></a>IDiaSymbol::get_hasInlAsm
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ruft ein Flag ab, das angibt, ob die Funktion eine Inlineassembly enthält.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT get_hasInlAsm(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pFlag`  
 vorgenommen Gibt zurück, `TRUE` Wenn die Funktion über eine Inlineassembly verfügt; andernfalls wird zurückgegeben `FALSE` .  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn erfolgreich, wird zurückgegeben `S_OK` ; andernfalls wird `S_FALSE` oder ein Fehlercode zurückgegeben.  
  
> [!NOTE]
> Der Rückgabewert `S_FALSE` bedeutet, dass die Eigenschaft für das Symbol nicht verfügbar ist.  
  
## <a name="requirements"></a>Anforderungen  
  
|Anforderung|BESCHREIBUNG|  
|-----------------|-----------------|  
|Header:|dia2.h|  
|Version:|Dia SDK v 8.0|  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
